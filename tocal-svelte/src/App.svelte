<script>
  import Calendar from "./lib/calendar/Calendar.svelte";
  import Todo from "./lib/todo/Todo.svelte";
  import Notes from "./lib/notes/Notes.svelte";
</script>

<main>
  <h1>ToCal</h1>
  <div id="leftRightCont">
    <div id="leftDiv">
      <Calendar />
    </div>
    <div id="rightDiv">
      <Todo />
      <Notes />
    </div>
  </div>
</main>

<style>
</style>
