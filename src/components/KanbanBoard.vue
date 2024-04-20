<template>
  <div class="kanban-board">
    <div v-for="(cards, status) in board" :key="status" class="kanban-column">
      <h3>{{ status }}</h3>
      <draggable class="drag-area" :list="cards" group="cards" item-key="id">
        <template #item="{ element }">
          <div class="kanban-card">
            <h4>{{ element.title }}</h4>
            <p>{{ element.description }}</p>
          </div>
        </template>
      </draggable>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  components: {
    draggable,
  },
  data() {
    return {
      board: {
        "To Do": [
          { id: 1, title: "Task 1", description: "Description of task 1" },
          { id: 2, title: "Task 2", description: "Description of task 2" },
        ],
        "In Progress": [
          { id: 3, title: "Task 3", description: "Description of task 3" },
        ],
        Done: [
          { id: 4, title: "Task 4", description: "Description of task 4" },
        ],
      },
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Work+Sans:wght@400;600&display=swap");

.kanban-board {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin: 0 auto;
  padding: 2rem;
  background-color: #fff9f3;
  font-family: "Work Sans", sans-serif;
}

.kanban-column {
  flex-basis: calc(33.333% - 2rem);
  box-sizing: border-box;
  margin: 1rem;
  background-color: #ffecbe;
  border-radius: 15px;
  box-shadow: 0 4px 8px rgba(56, 16, 16, 0.2);
  padding: 1rem;
  transition: background-color 0.3s, box-shadow 0.3s;
}

.kanban-column h3 {
  text-align: center;
  color: #381010;
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  border-bottom: 3px solid #f2b8b4;
}

.kanban-column:hover {
  background-color: #f2b8b4;
  box-shadow: 0 6px 12px rgba(56, 16, 16, 0.3);
}

.drag-area {
  min-height: 50px;
}

.kanban-card {
  background-color: #ffffff;
  border: 2px solid #f2b8b4;
  box-shadow: 0 2px 4px rgba(56, 16, 16, 0.1);
  margin-bottom: 1rem;
  padding: 0.8rem;
  border-radius: 10px;
  transition: transform 0.3s ease, box-shadow 0.3s;
}

.kanban-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 10px rgba(56, 16, 16, 0.15);
}

.kanban-card h4 {
  color: #381010;
  margin-bottom: 0.5rem;
}

.kanban-card p {
  color: #381010;
  font-size: 0.9rem;
}

@media (max-width: 1024px) {
  .kanban-board {
    justify-content: space-around;
  }
  .kanban-column {
    flex-basis: calc(50% - 1rem);
  }
}

@media (max-width: 768px) {
  .kanban-board {
    justify-content: center;
  }
  .kanban-column {
    flex-basis: 100%;
    margin: 1rem 0;
  }
}

@media (max-width: 480px) {
  .kanban-card {
    padding: 0.5rem;
  }
  .kanban-card h4 {
    font-size: 1rem;
  }
  .kanban-card p {
    font-size: 0.8rem;
  }
}
</style>
