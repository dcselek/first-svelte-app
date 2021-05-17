<script>
  import {
    Col,
    Container,
    Row,
    Button,
    Card,
    Spinner,
    CardHeader,
    CardTitle,
    CardBody,
    CardSubtitle,
    CardText,
    Badge,
    Modal,
    ModalHeader,
    ModalBody,
    Label,
  } from "sveltestrap";

  import { submitWrite } from '../stores/stores'

  const colors = ["primary", "danger", "success", "warning"];

  let result = "info";

  function clickHandler(bla) {
    result = bla.target.textContent;
  }

  let open = false;

  function toggle() {
    open = !open;
  }

  let answer = "";

  function inputHandler() {
    submitWrite.set(answer);
  }
</script>

<svelte:head>
  <title>First Page</title>
</svelte:head>

<Container>
  <Row>
    <!-- each deneme -->
    {#each colors as color}
      <Col>
        <Button on:click={clickHandler} block {color}>{color}</Button>
      </Col>
    {/each}
  </Row>
  <!-- styling deneme -->
  <div class="can">
    <!-- if deneme -->
    {#if result === "info"}
      <Spinner color="info" />
    {:else}
      <Card inverse color={result}>
        <CardHeader>
          <CardTitle>DCSELEK</CardTitle>
        </CardHeader>
        <CardBody>
          <CardSubtitle>{result.toUpperCase()}</CardSubtitle>
          <CardText
            >Lorem ipsum dolor sit amet consectetur adipisicing elit. Nesciunt
            aliquam sapiente reiciendis obcaecati repudiandae laudantium itaque
            est ut alias earum dignissimos, tempore voluptates quibusdam
            officiis, veniam adipisci minima? Dignissimos, expedita?</CardText
          >
        </CardBody>
      </Card>
    {/if}
  </div>
  <Row style="align-items: center; justify-content: center; padding: 3rem">
    <Col xs="auto">
      <h1>Hello <Badge color={result}>Svelte!</Badge></h1>
    </Col>
    <Col xs="auto">
      <h1>What's Up <Badge color={result}>Buddy!</Badge></h1>
    </Col>
    <Col xs="auto">
      <Badge color={result}>I feel so excited cause i learn new things 😮</Badge
      >
    </Col>
  </Row>
  <Row style="align-items: center; justify-content: center;">
    <Col xs="auto">
      <Button color="dark" on:click={toggle}>Click Me!</Button>
      <Modal isOpen={open} {toggle}>
        <ModalHeader {toggle}>This is a Header</ModalHeader>
        <ModalBody style="color: purple"
          >Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam
          nam officia asperiores enim eveniet explicabo cum, recusandae
          distinctio ad, voluptatem aliquam optio voluptatum. Repellendus,
          corrupti blanditiis? A cupiditate at quam.</ModalBody
        >
      </Modal>
    </Col>
  </Row>
  <Row style="align-items: center; justify-content: center; margin-top: 45px;">
    <Col xs="3">
      <Label>Example</Label>
      <form on:submit|preventDefault={inputHandler}>
        <input
          style="width: -webkit-fill-available;"
          name="anything"
          id="exampleAnything"
          placeholder="enter anything"
          bind:value={answer}
        />
        <Button
          block
          type="submit"
          for="exampleAnything"
          color="danger"
          style="margin-top: 8px;">Submit</Button
        >
      </form>
    </Col>
  </Row>
</Container>

<style>
  .can {
    display: flex;
    margin-top: 15px;
    justify-content: center;
  }
</style>
