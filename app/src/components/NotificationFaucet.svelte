<script>
  import { onDestroy } from "svelte";
  import { notification } from "../stores.js";
  import Notification from "../components/Notification.svelte";
  import { NOTIFICATION_TIMEOUT } from "../config.js";
  import { blur } from "svelte/transition";

  let messages = [];

  const unsubscribe = notification.subscribe(message => {
    if (!message) {
      return;
    }

    let id = Math.random();
    messages = [
      ...messages,
      { id: id, message: message.text, level: message.level }
    ];
    notification.set();
    setTimeout(() => {
      remove(id);
    }, NOTIFICATION_TIMEOUT);
  });

  const remove = id => {
    messages = messages.filter(m => m.id != id);
  };

  onDestroy(() => {
    unsubscribe();
  });
</script>

<style>
  .wrapper {
    position: absolute;
    z-index: 1001;
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    padding: 0 80px 0 80px;
  }

  .notification {
    margin-bottom: 8px;
  }
</style>

<div class="wrapper">
  {#each messages as message}
    <div class="notification" transition:blur={{ duration: 300 }}>
      <Notification
        level={message.level}
        on:click={() => {
          remove(message.id);
        }}>
        {message.message}
      </Notification>
    </div>
  {/each}
</div>
