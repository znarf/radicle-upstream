<script>
  import TxRow from "./TxRow.svelte";
  import { Button, Title, Caption, Rad, Avatar } from "../../DesignSystem";
  import RowLayout from "../../layouts/helpers/Row.svelte";

  export let onNextStep = null;
  export let onPreviousStep = null;
</script>

<style>
  .button-row {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    margin-top: 48px;
  }
</style>

<TxRow style="margin-bottom: 48px;" active={true}>
  <div slot="left">
    <Avatar title="Your personal wallet"/>
  </div>

  <div slot="right">
    <Rad amount={200} style="margin-right: 24px" />
  </div>
</TxRow>

<Caption style="color: var(--color-darkgray); margin-bottom: 24px">
  Project wallets
</Caption>
<TxRow style="margin-bottom: 16px">
  <div slot="left">
    <Avatar
      imageUrl="https://avatars.dicebear.com/v2/jdenticon/project1.svg"
      variant="project"
      title="Monadic wallet"/>
  </div>

  <div slot="right">
    <Rad amount={2387} style="margin-right: 24px" />
  </div>
</TxRow>

<TxRow style="margin-bottom: 16px">
  <div slot="left">
    <Avatar
      imageUrl="https://avatars.dicebear.com/v2/jdenticon/project2.svg"
      variant="project"
      title="Radicle wallet" />
  </div>

  <div slot="right">
    <Rad amount={2387} style="margin-right: 24px" />
  </div>
</TxRow>

<RowLayout style="margin-top: 48px;">
  <div slot="left">
    <Button
      disabled={false}
      on:click={onPreviousStep}
      variant="outline"
      style="margin-right: 24px">
      Back
    </Button>
  </div>
  <div slot="right">
    <Button disabled={false} on:click={onNextStep} variant="primary">Next</Button>
  </div>
</RowLayout>
