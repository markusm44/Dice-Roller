<script lang="ts">
import {
  SvelteUIProvider
} from '@svelteuidev/core';
import {
  Button,
  Flex,
  TextInput,
  Space,
  Code,
  Title,
} from '@svelteuidev/core';
let numOfRolls = 1;
let selected = "";
let result = "";
let total = 0;

let d20 = false;
let d12 = false;
let d10 = false;
let d8 = false;
let d6 = false;
let d4 = false;
let d100 = false;

const getRandomInt = (max) => {
  return Math.floor((Math.random() * max) + 1);
}

const reset = () => {
  d20 = false;
  d12 = false;
  d10 = false;
  d8 = false;
  d6 = false;
  d4 = false;
  d100 = false;
}

const roll = () => {
  if (!d20 && !d12 && !d10 && !d8 && !d6 && !d4 && !d100) {
    alert("You need to select a die type to roll!");
    return;
  }

  switch (selected) {
    case "d20":
      total = 0;
      for (let i = 0; i < numOfRolls; i++) {
        let num = getRandomInt(20)
        total = total + num;
        if (i > 0) {
          result = `${result} / ${num}`
        } else {
          result = String(num);
        }
      }
      break;
    case "d12":
      total = 0;
      for (let i = 0; i < numOfRolls; i++) {
        let num = getRandomInt(12)
        total = total + num;
        if (i > 0) {
          result = `${result} / ${num}`
        } else {
          result = String(num);
        }
      }
      break;
    case "d10":
      total = 0;
      for (let i = 0; i < numOfRolls; i++) {
        let num = getRandomInt(10)
        total = total + num; 
        if (i > 0) {
          result = `${result} / ${num}`
        } else {
          result = String(num);
        }
      }
      break;
    case "d8":
      total = 0;
      for (let i = 0; i < numOfRolls; i++) {
        let num = getRandomInt(8)
        total = total + num;
        if (i > 0) {
          result = `${result} / ${num}`
        } else {
          result = String(num);
        }
      }
      break;
    case "d6":
      total = 0;
      for (let i = 0; i < numOfRolls; i++) {
        let num = getRandomInt(6)
        total = total + num;
        if (i > 0) {
          result = `${result} / ${num}`
        } else {
          result = String(num);
        }
      }
      break;
    case "d4":
      total = 0;
      for (let i = 0; i < numOfRolls; i++) {
        let num = getRandomInt(4)
        total = total + num;
        if (i > 0) {
          result = `${result} / ${num}`
        } else {
          result = String(num);
        }
      }
      break;
    case "d100":
      total = 0;
      for (let i = 0; i < numOfRolls; i++) {
        let num = getRandomInt(100)
        total = total + num;
        if (i > 0) {
          result = `${result} / ${num}`
        } else {
          result = String(num);
        }
      }
      break;
  }
}
</script>

<SvelteUIProvider themeObserver="dark">
  <div class="main-container">
    <div class="content">
      <TextInput
        label="Number of Rolls"
        size="md"
        required={false}
        bind:value={numOfRolls}
      />
      <Space h="lg" />
      <Flex justify="center" gap="md">
        <Button
          ripple
          on:click={() => {reset()}}
          on:click={() => {d20 = true}}
          on:click={() => {selected = "d20"}}
          disabled={d20}
        >d20</Button>
        <Button
          ripple
          on:click={() => {reset()}}
          on:click={() => {d12 = true}}
          on:click={() => {selected = "d12"}}
          disabled={d12}
        >d12</Button>
        <Button
          ripple
          on:click={() => {reset()}}
          on:click={() => {d10 = true}}
          on:click={() => {selected = "d10"}}
          disabled={d10}
        >d10</Button>
        <Button
          ripple
          on:click={() => {reset()}}
          on:click={() => {d8 = true}}
          on:click={() => {selected = "d8"}}
          disabled={d8}
        >d8</Button>
        <Button
          ripple
          on:click={() => {reset()}}
          on:click={() => {d6 = true}}
          on:click={() => {selected = "d6"}}
          disabled={d6}
        >d6</Button>
        <Button
          ripple
          on:click={() => {reset()}}
          on:click={() => {d4 = true}}
          on:click={() => {selected = "d4"}}
          disabled={d4}
        >d4</Button>
        <Button
          ripple
          on:click={() => {reset()}}
          on:click={() => {d100 = true}}
          on:click={() => {selected = "d100"}}
          disabled={d100}
        >d100</Button>
      </Flex>
      <Space h="lg" />
      <Button variant="outline" size="md" uppercase ripple
        on:click={() => {roll()}}
      >
        Roll
      </Button>
      <Space h="lg" />
      <Code block copy message={result}>
        {result}
      </Code>
      <Title>Total: {total}</Title>
    </div>
  </div>
</SvelteUIProvider>

<style>
  .main-container {
    width: 100%;
    height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;
  }

  .content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>
