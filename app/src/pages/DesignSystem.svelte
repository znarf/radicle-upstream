<script>
  import {
    Button,
    Text,
    Title,
    Numeric,
    Caption,
    Icon,
    TextInput,
    Select,
    CheckboxInput,
    Avatar
  } from "../DesignSystem";

  import Notification from "../components/Notification.svelte";

  import { link } from "svelte-spa-router";

  let colors = Array.from(document.styleSheets)
    .filter(
      sheet =>
        sheet.href === null || sheet.href.startsWith(window.location.origin)
    )
    .reduce(
      (acc, sheet) =>
        (acc = [
          ...acc,
          ...Array.from(sheet.cssRules).reduce(
            (def, rule) =>
              (def =
                rule.selectorText === ":root"
                  ? [
                      ...def,
                      ...Array.from(rule.style).filter(name =>
                        name.startsWith("--color")
                      )
                    ]
                  : def),
            []
          )
        ]),
      []
    );
</script>

<style>
  div,
  table {
    margin-bottom: 32px;
  }

  td {
    vertical-align: middle;
    padding: 5px;
  }

  .icons {
    display: flex;
    align-items: center;
  }

  .layout {
    margin: 160px;
  }

  .section {
    margin-bottom: 180px;
    display: grid;
    grid-template-columns: 342px auto 100px;
  }

  .first-column {
    grid-column-start: 1;
    margin-right: 90px;
  }

  .row {
    display: flex;
    margin-bottom: 34px;
    align-items: baseline;
  }
</style>

<div class="layout">
  <div class="section">
    <div class="first-column">
      <Title size="big">Colors</Title>
      <Text style="color: var(--color-gray)">
        Primary, secondary and grays
      </Text>
    </div>
    <div class="second-column">
      {#each colors as color}
        <Text style="background-color: var({color})">
          {color}
        </Text>
      {/each}
    </div>
  </div>

  <div class="section">
    <div class="first-column">
      <Title size="big">Typography</Title>
      <Text style="color: var(--color-gray)">
        Using GT America and GT America Mono from Grill Type
      </Text>
    </div>
    <div class="second-column">
      <Title size="huge">Open Source Coin</Title>
      <Title size="big">Open Source Coin</Title>
      <Title>Open Source Coin</Title>

      <Text>Open Source Coin</Text>
      <Text size="small" weight="bold">Open Source Coin</Text>
      <Text size="small">Open Source Coin</Text>

      <Caption>Open Source Coin</Caption>

      <Numeric size="big">0123456789</Numeric>
      <Numeric>0123456789</Numeric>
      <Numeric size="small">0123456789</Numeric>

      <Caption>Open Source Coin</Caption>
    </div>
  </div>

  <div class="section">
    <div class="first-column">
      <Title size="big">Icons</Title>
      <Text style="color: var(--color-gray)">
        Icons at 16px, 24px, 36px and 64px width and height with 2px stroke
        weight, multiple color variations
      </Text>
    </div>
    <div class="second-column">
      <Icon.Branch />
      <Icon.Carret />
      <Icon.Check />
      <Icon.Commit />
      <Icon.Cross />
      <Icon.CrossBig />
      <Icon.Ellipse />
      <Icon.EllipseBig />
      <Icon.Ellipses />
      <Icon.Feed />
      <Icon.File />
      <Icon.Folder />
      <Icon.Fund />
      <Icon.Graph />
      <Icon.Home />
      <Icon.Important />
      <Icon.Inbox />
      <Icon.Info />
      <Icon.Member />
      <Icon.Minus />
      <Icon.Plus />
      <Icon.Projects />
      <Icon.Search />
      <Icon.SearchSmall />
      <Icon.Source />
    </div>
  </div>

  <div class="section">
    <div class="first-column">
      <Title size="big">Buttons</Title>
      <Text style="color: var(--color-gray)">
        Vanilla, Primary, Secondary, Cancel, disabled state
      </Text>
    </div>
    <div class="second-column">
      <table>
        <thead>
          <tr>
            <td>
              <Caption>Variant</Caption>
            </td>
            <td>
              <Caption>Disabled</Caption>
            </td>
            <td>
              <Caption>Variant</Caption>
            </td>
            <td>
              <Caption>Disabled</Caption>
            </td>
          </tr>
        </thead>
        <tr>
          <td>
            <Button variant="vanilla">Vanilla</Button>
          </td>
          <td>
            <Button variant="vanilla" disabled>Vanilla</Button>
          </td>
          <td>
            <Button icon={Icon.Plus} variant="vanilla">Vanilla</Button>
          </td>
          <td>
            <Button icon={Icon.Plus} variant="vanilla" disabled>Vanilla</Button>
          </td>
        </tr>

        <tr>
          <td>
            <Button variant="primary">Primary</Button>
          </td>
          <td>
            <Button variant="primary" disabled>Primary</Button>
          </td>
          <td>
            <Button icon={Icon.Minus} variant="primary">Primary</Button>
          </td>
          <td>
            <Button icon={Icon.Minus} variant="primary" disabled>
              Primary
            </Button>
          </td>
        </tr>

        <tr>
          <td>
            <Button variant="secondary">Secondary</Button>
          </td>
          <td>
            <Button variant="secondary" disabled>Secondary</Button>
          </td>
          <td>
            <Button icon={Icon.SearchSmall} variant="secondary">
              Secondary
            </Button>
          </td>
          <td>
            <Button icon={Icon.SearchSmall} variant="secondary" disabled>
              Secondary
            </Button>
          </td>
        </tr>

        <tr>
          <td>
            <Button variant="transparent">Transparent</Button>
          </td>
          <td>
            <Button variant="transparent" disabled>Transparent</Button>
          </td>
          <td>
            <Button icon={Icon.Check} variant="transparent">Transparent</Button>
          </td>
          <td>
            <Button icon={Icon.Check} variant="transparent" disabled>
              Transparent
            </Button>
          </td>
        </tr>

        <tr>
          <td>
            <Button variant="outline">Outline</Button>
          </td>
          <td>
            <Button variant="outline" disabled>Outline</Button>
          </td>
          <td>
            <Button icon={Icon.Graph} variant="outline">Outline</Button>
          </td>
          <td>
            <Button icon={Icon.Graph} variant="outline" disabled>
              Outline
            </Button>
          </td>
        </tr>
      </table>

      <table>
        <thead>
          <tr>
            <td>
              <Caption>Variant</Caption>
            </td>
            <td>
              <Caption>Disabled</Caption>
            </td>
            <td>
              <Caption>Variant</Caption>
            </td>
            <td>
              <Caption>Disabled</Caption>
            </td>
          </tr>
        </thead>
        <tr>
          <td>
            <Button size="small" variant="vanilla">Vanilla</Button>
          </td>
          <td>
            <Button size="small" variant="vanilla" disabled>Vanilla</Button>
          </td>
          <td>
            <Button size="small" icon={Icon.Plus} variant="vanilla">
              Vanilla
            </Button>
          </td>
          <td>
            <Button size="small" icon={Icon.Plus} variant="vanilla" disabled>
              Vanilla
            </Button>
          </td>
        </tr>

        <tr>
          <td>
            <Button size="small" variant="primary">Primary</Button>
          </td>
          <td>
            <Button size="small" variant="primary" disabled>Primary</Button>
          </td>
          <td>
            <Button size="small" icon={Icon.Minus} variant="primary">
              Primary
            </Button>
          </td>
          <td>
            <Button size="small" icon={Icon.Minus} variant="primary" disabled>
              Primary
            </Button>
          </td>
        </tr>

        <tr>
          <td>
            <Button size="small" variant="secondary">Secondary</Button>
          </td>
          <td>
            <Button size="small" variant="secondary" disabled>Secondary</Button>
          </td>
          <td>
            <Button size="small" icon={Icon.SearchSmall} variant="secondary">
              Secondary
            </Button>
          </td>
          <td>
            <Button
              size="small"
              icon={Icon.SearchSmall}
              variant="secondary"
              disabled>
              Secondary
            </Button>
          </td>
        </tr>

        <tr>
          <td>
            <Button size="small" variant="transparent">Transparent</Button>
          </td>
          <td>
            <Button size="small" variant="transparent" disabled>
              Transparent
            </Button>
          </td>
          <td>
            <Button size="small" icon={Icon.Check} variant="transparent">
              Transparent
            </Button>
          </td>
          <td>
            <Button
              size="small"
              icon={Icon.Check}
              variant="transparent"
              disabled>
              Transparent
            </Button>
          </td>
        </tr>

        <tr>
          <td>
            <Button size="small" variant="outline">Outline</Button>
          </td>
          <td>
            <Button size="small" variant="outline" disabled>Outline</Button>
          </td>
          <td>
            <Button size="small" icon={Icon.Graph} variant="outline">
              Outline
            </Button>
          </td>
          <td>
            <Button size="small" icon={Icon.Graph} variant="outline" disabled>
              Outline
            </Button>
          </td>
        </tr>
      </table>
    </div>
  </div>

  <div class="section">
    <div class="first-column">
      <Title size="big">Form elements</Title>
      <Text style="color: var(--color-gray)">
        Inputs, text areas, dropdowns, etc.
      </Text>
    </div>
    <div class="second-column">
      <div class="row">
        <TextInput placeholder="Hey, I'm an input." />
      </div>

      <div class="row">
        <Select items={['master', 'dev']} value={'dev'} />
        <Select disabled items={['master', 'dev']} value={'dev'} />
      </div>

      <div class="row">
        <CheckboxInput>How about a checkbox?</CheckboxInput>
      </div>
    </div>
  </div>

  <div class="section">
    <div class="first-column">
      <Title size="big">Notifications</Title>
      <Text style="color: var(--color-gray)">
        Info, Warnings and Errors
      </Text>
    </div>
    <div class="second-column">
      <div class="row">
        <Notification>
          This is harmless, but you should know anyway.
        </Notification>
      </div>
      <div class="row">
        <Notification level="warning">
          This is slightly concerning.
        </Notification>
      </div>
      <div class="row">
        <Notification level="error">Something bad happened, halp!</Notification>
      </div>
    </div>
  </div>

  <div class="section">
    <div class="first-column">
      <Title size="big">Avatars</Title>
      <Text style="color: var(--color-gray)">
        User, project, etc avatars in various sizes and shapes.
      </Text>
    </div>
    <div class="second-column">
      <div class="row">
        <Avatar />
        <Avatar size="big" />
        <Avatar
          imageUrl="https://avatars.dicebear.com/v2/avataaars/gWIIBkeCYYZFCPhBp3Cl.svg" />
        <Avatar
          imageUrl="https://avatars.dicebear.com/v2/avataaars/gWIIBkeCYYZFCPhBp3Cl.svg"
          size="big" />
        <Avatar
          imageUrl="https://avatars.dicebear.com/v2/jdenticon/one.svg"
          variant="project" />
        <Avatar
          imageUrl="https://avatars.dicebear.com/v2/jdenticon/two.svg"
          variant="project"
          size="big" />
      </div>
      <div class="row">
        <Avatar title="My name"/>
        <Avatar size="big" title="My name"/>
    </div>
    </div>
  </div>
</div>
