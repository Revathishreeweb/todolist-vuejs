<template>
  <div class="container" style="max-width: 600px">
    <!----- heading start ------>
    <h2 class="text-center">TodoApp</h2>

    <!--- input ------>
    <div class="d-flex mt-5">
      <input
        type="text"
        v-model="task"
        placeholder="Enter task"
        class="w-100 form-control"
      />
      <button class="btn btn-primary">Submit</button>
    </div>

    <!----Task table---->
    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col" style="width: 120px">Status</th>
          <th scope="col" class="text-center">Edit</th>
          <th scope="col" class="text-center">Delete</th>
        </tr>
        <tr>
          <td>add anything here</td>
          <td>To do</td>
          <td>
            <div>
              <span class="fa fa-pen"></span>
            </div>
            <div>
              <span class="fa fa-delete"></span>
            </div>
          </td>
        </tr>
      </thead>
    </table>
  </div>
</template>

<script>
export default {
  name: "TodoApp",
};
</script>

