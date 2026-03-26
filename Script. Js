const defaultActivities = [
  {
    id: 1,
    name: "Learn HTML",
    description: "Study basic HTML tags",
    completed: false
  },
  {
    id: 2,
    name: "Practice CSS",
    description: "Work on styling and layouts",
    completed: false
  },
  {
    id: 3,
    name: "JavaScript Basics",
    description: "Understand variables and functions",
    completed: false
  },
  {
    id: 4,
    name: "Build Mini Project",
    description: "Create a simple webpage",
    completed: false
  }
];

// Load from localStorage or default
let activities = JSON.parse(localStorage.getItem("activities")) || defaultActivities;

function saveData() {
  localStorage.setItem("activities", JSON.stringify(activities));
}

function toggleStatus(id) {
  activities = activities.map(activity => {
    if (activity.id === id) {
      activity.completed = !activity.completed;
    }
    return activity;
  });

  saveData();
  renderActivities();
}

function renderActivities() {
  const list = document.getElementById("activityList");
  list.innerHTML = "";

  activities.forEach(activity => {
    const div = document.createElement("div");
    div.className = "activity";

    div.innerHTML = `
      <h3>${activity.name}</h3>
      <p>${activity.description}</p>
      <p class="status ${activity.completed ? "completed" : "pending"}">
        ${activity.completed ? "Completed" : "Pending"}
      </p>
      <button onclick="toggleStatus(${activity.id})">
        ${activity.completed ? "Undo" : "Mark as Completed"}
      </button>
    `;

    list.appendChild(div);
  });

  updateProgress();
}

function updateProgress() {
  const completed = activities.filter(a => a.completed).length;
  const total = activities.length;

  document.getElementById("progressText").innerText =
    `${completed} / ${total} Completed`;

  const percentage = (completed / total) * 100;
  document.getElementById("progressFill").style.width = percentage + "%";
}

// Initial render
renderActivities();
