cat > package.json <<'EOF'
{
  "name": "kid-planner",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite --host 0.0.0.0",
    "build": "vite build",
    "preview": "vite preview --host 0.0.0.0"
  },
  "dependencies": {
    "@vitejs/plugin-react": "latest",
    "vite": "latest",
    "react": "latest",
    "react-dom": "latest",
    "lucide-react": "latest",
    "framer-motion": "latest"
  },
  "devDependencies": {}
}
EOF

cat > index.html <<'EOF'
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Kid Weekly Planner</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
EOF

mkdir -p src

cat > src/main.jsx <<'EOF'
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./index.css";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
EOF

cat > vite.config.js <<'EOF'
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()]
});
EOF

cat > src/index.css <<'EOF'
* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  min-width: 320px;
  min-height: 100vh;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", sans-serif;
  background: #f8fafc;
}

button,
input {
  font-family: inherit;
}

button {
  cursor: pointer;
}

.app {
  min-height: 100vh;
  background: linear-gradient(135deg, #f8fafc 0%, #eef2ff 52%, #fff7ed 100%);
  color: #0f172a;
  padding: 28px;
}

.container {
  max-width: 1400px;
  margin: 0 auto;
}

.header {
  background: rgba(255, 255, 255, 0.9);
  border: 1px solid #e2e8f0;
  border-radius: 34px;
  padding: 32px;
  box-shadow: 0 20px 50px rgba(15, 23, 42, 0.1);
  display: flex;
  justify-content: space-between;
  gap: 28px;
  flex-wrap: wrap;
}

.badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: #e0e7ff;
  color: #4338ca;
  padding: 10px 16px;
  border-radius: 999px;
  font-weight: 900;
  margin-bottom: 16px;
}

.title {
  font-size: 52px;
  line-height: 1;
  margin: 0;
  font-weight: 950;
}

.name-input {
  font-size: 42px;
  font-weight: 950;
  width: 260px;
  border: 0;
  border-radius: 18px;
  background: #fef3c7;
  color: #b45309;
  padding: 6px 12px;
  outline: none;
}

.subtitle {
  font-size: 18px;
  color: #64748b;
  font-weight: 700;
  max-width: 680px;
}

.stat-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 12px;
  min-width: 480px;
}

.stat-card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 24px;
  padding: 18px;
}

.stat-icon {
  width: 42px;
  height: 42px;
  border-radius: 16px;
  background: white;
  color: #4f46e5;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 10px;
}

.stat-value {
  display: block;
  font-size: 26px;
  font-weight: 950;
}

.stat-label {
  display: block;
  color: #64748b;
  font-size: 13px;
  font-weight: 900;
  text-transform: uppercase;
}

.today-hero {
  margin-top: 24px;
  background: linear-gradient(
    135deg,
    rgba(79, 70, 229, 0.12) 0%,
    rgba(254, 243, 199, 0.95) 100%
  );
  border: 1px solid #c7d2fe;
  border-radius: 36px;
  padding: 32px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 28px;
  flex-wrap: wrap;
  box-shadow: 0 20px 50px rgba(79, 70, 229, 0.12);
}

.today-label {
  display: inline-block;
  background: #312e81;
  color: white;
  padding: 9px 15px;
  border-radius: 999px;
  font-weight: 950;
  font-size: 13px;
  letter-spacing: 1px;
}

.today-title {
  font-size: 42px;
  line-height: 1.1;
  margin: 16px 0 10px;
  font-weight: 950;
}

.today-text {
  max-width: 680px;
  color: #475569;
  font-size: 18px;
  font-weight: 700;
}

.layout {
  display: grid;
  grid-template-columns: 1fr 390px;
  gap: 24px;
  margin-top: 24px;
}

.main,
.side {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.card {
  background: rgba(255, 255, 255, 0.94);
  border: 1px solid #e2e8f0;
  border-radius: 34px;
  padding: 26px;
  box-shadow: 0 18px 45px rgba(15, 23, 42, 0.09);
}

.section-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
  margin-bottom: 20px;
  flex-wrap: wrap;
}

.section-title {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 0;
  font-size: 26px;
  font-weight: 950;
}

.small-text {
  color: #64748b;
  font-weight: 700;
  margin-top: 6px;
}

.calendar-actions {
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}

.today-button {
  border: 1px solid #c7d2fe;
  background: #eef2ff;
  color: #4338ca;
  border-radius: 18px;
  padding: 12px 16px;
  font-weight: 950;
}

.outline-button {
  border: 1px solid #cbd5e1;
  background: white;
  border-radius: 18px;
  padding: 12px 16px;
  font-weight: 900;
  display: flex;
  align-items: center;
  gap: 8px;
}

.days-grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 12px;
}

.day-button {
  border: 1px solid #e2e8f0;
  background: #f8fafc;
  border-radius: 24px;
  padding: 18px;
  text-align: left;
  transition: all 0.2s;
}

.day-button strong {
  display: block;
  font-size: 17px;
  font-weight: 950;
}

.day-button span {
  display: block;
  font-size: 13px;
  font-weight: 800;
  margin-top: 4px;
}

.day-active {
  background: #4f46e5;
  color: white;
  border-color: #4f46e5;
  transform: translateY(-3px);
}

.mini-bar {
  height: 8px;
  background: rgba(148, 163, 184, 0.35);
  border-radius: 999px;
  margin-top: 12px;
  overflow: hidden;
}

.mini-bar-fill {
  height: 100%;
  border-radius: 999px;
  background: #4f46e5;
}

.daily-progress-hero {
  display: grid;
  grid-template-columns: 1.2fr 320px;
  gap: 24px;
  align-items: center;
  padding: 24px;
  margin-bottom: 24px;
  border-radius: 30px;
  background: linear-gradient(
    135deg,
    rgba(79, 70, 229, 0.08) 0%,
    rgba(254, 243, 199, 0.75) 100%
  );
  border: 1px solid #e0e7ff;
}

.daily-tag {
  display: inline-block;
  background: #312e81;
  color: white;
  padding: 8px 14px;
  border-radius: 999px;
  font-weight: 950;
  font-size: 12px;
  letter-spacing: 1px;
}

.daily-title {
  font-size: 34px;
  line-height: 1.1;
  font-weight: 950;
  margin: 14px 0 8px;
}

.daily-text {
  font-size: 16px;
  color: #475569;
  font-weight: 700;
  margin: 0 0 14px;
}

.daily-mini-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  max-width: 520px;
}

.mini-card {
  background: rgba(255, 255, 255, 0.88);
  border: 1px solid #dbeafe;
  border-radius: 20px;
  padding: 14px;
}

.mini-card span {
  display: block;
  font-size: 13px;
  color: #64748b;
  font-weight: 800;
}

.mini-card strong {
  display: block;
  font-size: 28px;
  font-weight: 950;
}

.day-message {
  display: inline-block;
  padding: 12px 16px;
  border-radius: 16px;
  background: white;
  border: 1px solid #e2e8f0;
  font-weight: 950;
  color: #4f46e5;
  margin-top: 14px;
}

.big-circle-wrap,
.circle-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
}

.big-circle {
  width: 250px;
  height: 250px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 16px 40px rgba(79, 70, 229, 0.18);
}

.big-circle-inner {
  width: 188px;
  height: 188px;
  background: white;
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-shadow: inset 0 0 0 1px #e2e8f0;
  text-align: center;
}

.big-percent {
  font-size: 46px;
  font-weight: 950;
  color: #1e1b4b;
  line-height: 1;
}

.big-label {
  font-size: 16px;
  font-weight: 900;
  color: #475569;
  margin-top: 8px;
}

.big-tasks {
  font-size: 15px;
  font-weight: 950;
  color: #4f46e5;
  margin-top: 8px;
}

.points-pill {
  background: #fef3c7;
  color: #b45309;
  padding: 12px 16px;
  border-radius: 18px;
  font-weight: 950;
}

.task-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.empty-box {
  border: 2px dashed #cbd5e1;
  border-radius: 26px;
  background: #f8fafc;
  padding: 40px;
  text-align: center;
  color: #64748b;
}

.task-item {
  border: 1px solid #e2e8f0;
  border-radius: 26px;
  padding: 16px;
  display: flex;
  align-items: center;
  gap: 14px;
  background: #f8fafc;
}

.task-done {
  background: #ecfdf5;
  border-color: #a7f3d0;
}

.check-button,
.delete-button {
  border: 0;
  background: transparent;
}

.task-text-box {
  flex: 1;
}

.task-text {
  font-size: 19px;
  font-weight: 950;
  color: #1e293b;
}

.task-text.done {
  color: #047857;
  text-decoration: line-through;
}

.task-points {
  margin-top: 8px;
  display: inline-flex;
  align-items: center;
  gap: 5px;
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 999px;
  padding: 6px 10px;
  font-weight: 900;
  color: #4f46e5;
}

.delete-button {
  color: #94a3b8;
}

.add-box {
  margin-top: 18px;
  background: linear-gradient(135deg, #e0e7ff, #fef3c7);
  padding: 16px;
  border-radius: 26px;
  display: grid;
  grid-template-columns: 1fr 110px 110px;
  gap: 10px;
}

.task-input,
.points-input {
  border: 0;
  border-radius: 18px;
  padding: 15px;
  font-size: 16px;
  font-weight: 800;
  outline: none;
}

.add-button {
  border: 0;
  background: #4f46e5;
  color: white;
  border-radius: 18px;
  font-weight: 950;
  font-size: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
}

.progress-box {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 28px;
  padding: 22px;
  text-align: center;
  margin-top: 20px;
}

.circle {
  width: 138px;
  height: 138px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
}

.circle-inner {
  width: 104px;
  height: 104px;
  background: white;
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.circle-inner strong {
  font-size: 25px;
  font-weight: 950;
}

.progress-bar-box {
  margin-top: 18px;
}

.progress-bar-top {
  display: flex;
  justify-content: space-between;
  font-size: 14px;
  margin-bottom: 8px;
}

.progress-track {
  height: 12px;
  background: #e2e8f0;
  border-radius: 999px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: #4f46e5;
  border-radius: 999px;
}

.score-box {
  margin-top: 22px;
  background: #4f46e5;
  color: white;
  border-radius: 28px;
  padding: 22px;
  display: flex;
  align-items: center;
  gap: 16px;
}

.score-box p {
  margin: 0;
  font-weight: 800;
}

.score-box strong {
  display: block;
  font-size: 34px;
  font-weight: 950;
}

.reward-box {
  background: #fffbeb;
  border: 1px solid #fde68a;
  border-radius: 24px;
  padding: 16px;
  margin-bottom: 16px;
}

.reward-input-row {
  display: grid;
  grid-template-columns: 1fr 90px;
  gap: 8px;
  margin-top: 8px;
}

.reward-input {
  border: 0;
  border-radius: 16px;
  padding: 12px;
  font-weight: 900;
  outline: none;
}

.reward-button {
  border: 0;
  border-radius: 16px;
  background: #f59e0b;
  color: white;
  font-weight: 950;
}

.reward-row {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 18px;
  padding: 12px 14px;
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}

.dark-card {
  background: #0f172a;
  color: white;
  border-radius: 34px;
  padding: 26px;
  box-shadow: 0 18px 45px rgba(15, 23, 42, 0.2);
}

.goal-input {
  width: 100%;
  border: 0;
  border-radius: 18px;
  padding: 14px;
  font-size: 18px;
  font-weight: 950;
  outline: none;
  margin-top: 8px;
}

@media (max-width: 1100px) {
  .layout {
    grid-template-columns: 1fr;
  }

  .daily-progress-hero {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 850px) {
  .stat-grid {
    grid-template-columns: repeat(2, 1fr);
    min-width: 0;
    width: 100%;
  }

  .days-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .add-box {
    grid-template-columns: 1fr;
  }

  .title {
    font-size: 40px;
  }

  .name-input {
    font-size: 34px;
    width: 210px;
  }

  .today-title {
    font-size: 32px;
  }
}
EOF

cat > src/App.jsx <<'EOF'
import React, { useEffect, useMemo, useState } from "react";
import { motion } from "framer-motion";
import {
  CalendarDays,
  CheckCircle2,
  Circle,
  Gift,
  Medal,
  Plus,
  Star,
  Target,
  Trash2,
  Trophy,
  BarChart3,
  RotateCcw,
  Sparkles,
} from "lucide-react";

const DAYS = [
  "Monday",
  "Tuesday",
  "Wednesday",
  "Thursday",
  "Friday",
  "Saturday",
  "Sunday",
];

const DAY_SHORT = {
  Monday: "Mon",
  Tuesday: "Tue",
  Wednesday: "Wed",
  Thursday: "Thu",
  Friday: "Fri",
  Saturday: "Sat",
  Sunday: "Sun",
};

const STORAGE_KEY = "kid-weekly-planner-complete-v1";

function createId() {
  if (crypto?.randomUUID) return crypto.randomUUID();
  return `${Date.now()}-${Math.random()}`;
}

function getTodayName() {
  const jsDay = new Date().getDay();

  const map = {
    0: "Sunday",
    1: "Monday",
    2: "Tuesday",
    3: "Wednesday",
    4: "Thursday",
    5: "Friday",
    6: "Saturday",
  };

  return map[jsDay];
}

const defaultData = {
  childName: "Alex",
  totalPoints: 0,
  weekGoal: 100,
  tasks: {
    Monday: [
      { id: "m1", text: "Read for 20 minutes", points: 10, done: false },
      { id: "m2", text: "Math practice", points: 15, done: false },
    ],
    Tuesday: [{ id: "t1", text: "Clean desk", points: 10, done: false }],
    Wednesday: [
      { id: "w1", text: "Exercise for 15 minutes", points: 10, done: false },
    ],
    Thursday: [{ id: "th1", text: "Review homework", points: 10, done: false }],
    Friday: [{ id: "f1", text: "Organize backpack", points: 10, done: false }],
    Saturday: [
      { id: "s1", text: "Help family with one task", points: 20, done: false },
    ],
    Sunday: [{ id: "su1", text: "Plan next week", points: 10, done: false }],
  },
};

function loadData() {
  try {
    const saved = localStorage.getItem(STORAGE_KEY);
    return saved ? JSON.parse(saved) : defaultData;
  } catch {
    return defaultData;
  }
}

export default function App() {
  const todayName = getTodayName();

  const [data, setData] = useState(loadData);
  const [selectedDay, setSelectedDay] = useState(todayName);
  const [newTask, setNewTask] = useState("");
  const [newPoints, setNewPoints] = useState(10);
  const [rewardCost, setRewardCost] = useState("");

  useEffect(() => {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
  }, [data]);

  const stats = useMemo(() => {
    const allTasks = DAYS.flatMap((day) => data.tasks[day] || []);
    const doneTasks = allTasks.filter((task) => task.done);

    const possiblePoints = allTasks.reduce(
      (sum, task) => sum + Number(task.points || 0),
      0
    );

    const earnedThisWeek = doneTasks.reduce(
      (sum, task) => sum + Number(task.points || 0),
      0
    );

    const completionPercent = allTasks.length
      ? Math.round((doneTasks.length / allTasks.length) * 100)
      : 0;

    const goalPercent = data.weekGoal
      ? Math.min(100, Math.round((earnedThisWeek / data.weekGoal) * 100))
      : 0;

    return {
      allTasks,
      doneTasks,
      possiblePoints,
      earnedThisWeek,
      completionPercent,
      goalPercent,
    };
  }, [data]);

  const selectedTasks = data.tasks[selectedDay] || [];
  const selectedDone = selectedTasks.filter((task) => task.done).length;
  const selectedTotal = selectedTasks.length;
  const selectedPercent = selectedTotal
    ? Math.round((selectedDone / selectedTotal) * 100)
    : 0;
  const remainingTasks = Math.max(0, selectedTotal - selectedDone);

  const todayTasks = data.tasks[todayName] || [];
  const todayDone = todayTasks.filter((task) => task.done).length;
  const todayPercent = todayTasks.length
    ? Math.round((todayDone / todayTasks.length) * 100)
    : 0;

  const isTodaySelected = selectedDay === todayName;

  function addTask() {
    const clean = newTask.trim();
    if (!clean) return;

    const task = {
      id: createId(),
      text: clean,
      points: Number(newPoints) || 10,
      done: false,
    };

    setData((prev) => ({
      ...prev,
      tasks: {
        ...prev.tasks,
        [selectedDay]: [...(prev.tasks[selectedDay] || []), task],
      },
    }));

    setNewTask("");
    setNewPoints(10);
  }

  function toggleTask(day, id) {
    setData((prev) => {
      let pointChange = 0;

      const nextTasks = prev.tasks[day].map((task) => {
        if (task.id !== id) return task;

        const nextDone = !task.done;
        pointChange = nextDone ? task.points : -task.points;

        return {
          ...task,
          done: nextDone,
        };
      });

      return {
        ...prev,
        totalPoints: Math.max(0, prev.totalPoints + pointChange),
        tasks: {
          ...prev.tasks,
          [day]: nextTasks,
        },
      };
    });
  }

  function deleteTask(day, id) {
    setData((prev) => {
      const removedTask = prev.tasks[day].find((task) => task.id === id);
      const pointChange = removedTask?.done ? -removedTask.points : 0;

      return {
        ...prev,
        totalPoints: Math.max(0, prev.totalPoints + pointChange),
        tasks: {
          ...prev.tasks,
          [day]: prev.tasks[day].filter((task) => task.id !== id),
        },
      };
    });
  }

  function resetWeek() {
    const ok = window.confirm("Reset this week's check-ins?");
    if (!ok) return;

    setData((prev) => ({
      ...prev,
      tasks: Object.fromEntries(
        DAYS.map((day) => [
          day,
          prev.tasks[day].map((task) => ({
            ...task,
            done: false,
          })),
        ])
      ),
    }));
  }

  function spendReward() {
    const cost = Number(rewardCost);
    if (!cost || cost <= 0) return;

    if (cost > data.totalPoints) {
      alert("Not enough points yet. Keep going!");
      return;
    }

    setData((prev) => ({
      ...prev,
      totalPoints: prev.totalPoints - cost,
    }));

    setRewardCost("");
  }

  const weekMessage =
    stats.completionPercent >= 90
      ? "Amazing week!"
      : stats.completionPercent >= 60
      ? "Great progress!"
      : stats.completionPercent >= 30
      ? "Keep going!"
      : "Start small today!";

  const dayMessage =
    selectedPercent === 100 && selectedTotal > 0
      ? "Awesome! All done!"
      : selectedPercent >= 70
      ? "Almost there!"
      : selectedPercent >= 30
      ? "Good job, keep going!"
      : selectedTotal === 0
      ? "No tasks yet"
      : "Let's get started!";

  return (
    <div className="app">
      <div className="container">
        <motion.header
          className="header"
          initial={{ opacity: 0, y: -12 }}
          animate={{ opacity: 1, y: 0 }}
        >
          <div>
            <div className="badge">
              <Sparkles size={18} />
              Weekly Mission Planner
            </div>

            <h1 className="title">
              Hi,{" "}
              <input
                className="name-input"
                value={data.childName}
                onChange={(e) =>
                  setData({
                    ...data,
                    childName: e.target.value,
                  })
                }
              />
            </h1>

            <p className="subtitle">
              Plan your week, finish daily missions, earn points, and unlock
              rewards.
            </p>
          </div>

          <div className="stat-grid">
            <StatCard
              icon={<Trophy size={24} />}
              label="Total Points"
              value={data.totalPoints}
            />
            <StatCard
              icon={<CheckCircle2 size={24} />}
              label="Done"
              value={`${stats.doneTasks.length}/${stats.allTasks.length}`}
            />
            <StatCard
              icon={<Star size={24} />}
              label="This Week"
              value={stats.earnedThisWeek}
            />
            <StatCard
              icon={<Target size={24} />}
              label="Goal"
              value={`${stats.goalPercent}%`}
            />
          </div>
        </motion.header>

        <section className="today-hero">
          <div>
            <div className="today-label">TODAY FOCUS</div>
            <h2 className="today-title">{todayName}'s Work Progress</h2>
            <p className="today-text">
              This large circle shows today’s real completion progress. It helps
              kids quickly understand how much work is finished today.
            </p>
          </div>

          <LargeDailyCircle
            percent={todayPercent}
            done={todayDone}
            total={todayTasks.length}
            label="Done Today"
          />
        </section>

        <div className="layout">
          <main className="main">
            <section className="card">
              <div className="section-top">
                <div>
                  <h2 className="section-title">
                    <CalendarDays size={26} />
                    Weekly Calendar
                  </h2>
                  <p className="small-text">
                    Click a day, add tasks, and check them off.
                  </p>
                </div>

                <div className="calendar-actions">
                  <button
                    onClick={() => setSelectedDay(todayName)}
                    className="today-button"
                  >
                    Today: {DAY_SHORT[todayName]}
                  </button>

                  <button onClick={resetWeek} className="outline-button">
                    <RotateCcw size={18} />
                    Reset Check-ins
                  </button>
                </div>
              </div>

              <div className="days-grid">
                {DAYS.map((day) => {
                  const dayTasks = data.tasks[day] || [];
                  const done = dayTasks.filter((task) => task.done).length;
                  const percent = dayTasks.length
                    ? Math.round((done / dayTasks.length) * 100)
                    : 0;
                  const active = selectedDay === day;

                  return (
                    <button
                      key={day}
                      onClick={() => setSelectedDay(day)}
                      className={`day-button ${active ? "day-active" : ""}`}
                    >
                      <strong>{DAY_SHORT[day]}</strong>
                      <span>
                        {done}/{dayTasks.length} tasks
                      </span>

                      <div className="mini-bar">
                        <div
                          className="mini-bar-fill"
                          style={{
                            width: `${percent}%`,
                            background: active ? "white" : "#4f46e5",
                          }}
                        />
                      </div>
                    </button>
                  );
                })}
              </div>
            </section>

            <section className="card">
              <div className="daily-progress-hero">
                <div>
                  <div className="daily-tag">
                    {isTodaySelected
                      ? "TODAY'S PROGRESS"
                      : `${selectedDay.toUpperCase()} PROGRESS`}
                  </div>

                  <h2 className="daily-title">
                    {selectedDay} Completion Progress
                  </h2>

                  <p className="daily-text">
                    This section shows the selected day’s completion progress.
                  </p>

                  <div className="daily-mini-grid">
                    <MiniCard label="Done" value={selectedDone} />
                    <MiniCard label="Total" value={selectedTotal} />
                    <MiniCard label="Left" value={remainingTasks} />
                  </div>

                  <div className="day-message">{dayMessage}</div>
                </div>

                <LargeDailyCircle
                  percent={selectedPercent}
                  done={selectedDone}
                  total={selectedTotal}
                  label="Selected Day"
                />
              </div>

              <div className="section-top">
                <div>
                  <h2 className="section-title">{selectedDay} Tasks</h2>
                  <p className="small-text">
                    Big buttons make check-ins easy.
                  </p>
                </div>

                <div className="points-pill">
                  {selectedTasks.reduce(
                    (sum, task) => sum + (task.done ? Number(task.points) : 0),
                    0
                  )}{" "}
                  pts today
                </div>
              </div>

              <div className="task-list">
                {selectedTasks.length === 0 && (
                  <div className="empty-box">
                    <Gift size={42} />
                    <h3>No tasks yet</h3>
                    <p>Add one below to start earning points.</p>
                  </div>
                )}

                {selectedTasks.map((task) => (
                  <motion.div
                    key={task.id}
                    className={`task-item ${task.done ? "task-done" : ""}`}
                    initial={{ opacity: 0, y: 8 }}
                    animate={{ opacity: 1, y: 0 }}
                  >
                    <button
                      onClick={() => toggleTask(selectedDay, task.id)}
                      className="check-button"
                    >
                      {task.done ? (
                        <CheckCircle2 size={34} color="#059669" />
                      ) : (
                        <Circle size={34} color="#94a3b8" />
                      )}
                    </button>

                    <div className="task-text-box">
                      <div className={`task-text ${task.done ? "done" : ""}`}>
                        {task.text}
                      </div>

                      <div className="task-points">
                        <Star size={14} />
                        {task.points} points
                      </div>
                    </div>

                    <button
                      onClick={() => deleteTask(selectedDay, task.id)}
                      className="delete-button"
                    >
                      <Trash2 size={22} />
                    </button>
                  </motion.div>
                ))}
              </div>

              <div className="add-box">
                <input
                  className="task-input"
                  value={newTask}
                  onChange={(e) => setNewTask(e.target.value)}
                  onKeyDown={(e) => {
                    if (e.key === "Enter") addTask();
                  }}
                  placeholder="Add a task, like: Practice piano for 15 minutes"
                />

                <input
                  className="points-input"
                  type="number"
                  min="1"
                  value={newPoints}
                  onChange={(e) => setNewPoints(e.target.value)}
                />

                <button onClick={addTask} className="add-button">
                  <Plus size={22} />
                  Add
                </button>
              </div>
            </section>
          </main>

          <aside className="side">
            <section className="card">
              <h2 className="section-title">
                <BarChart3 size={26} />
                Dashboard
              </h2>

              <div className="progress-box">
                <ProgressCircle percent={stats.completionPercent} />
                <h3>{weekMessage}</h3>
                <p>
                  {stats.doneTasks.length} of {stats.allTasks.length} tasks
                  finished
                </p>
              </div>

              <ProgressBar
                label="Weekly Points Goal"
                value={stats.goalPercent}
                detail={`${stats.earnedThisWeek}/${data.weekGoal} pts`}
              />

              <ProgressBar
                label="Point Opportunity"
                value={
                  stats.possiblePoints
                    ? Math.round(
                        (stats.earnedThisWeek / stats.possiblePoints) * 100
                      )
                    : 0
                }
                detail={`${stats.earnedThisWeek}/${stats.possiblePoints} pts`}
              />

              <div className="score-box">
                <Medal size={44} />
                <div>
                  <p>Lifetime Score</p>
                  <strong>{data.totalPoints}</strong>
                </div>
              </div>
            </section>

            <section className="card">
              <h2 className="section-title">
                <Gift size={26} />
                Rewards
              </h2>

              <p className="small-text">
                Parents can decide rewards. Example: 50 points = extra fun
                time.
              </p>

              <div className="reward-box">
                <label>Spend points</label>
                <div className="reward-input-row">
                  <input
                    className="reward-input"
                    type="number"
                    value={rewardCost}
                    onChange={(e) => setRewardCost(e.target.value)}
                    placeholder="50"
                  />
                  <button onClick={spendReward} className="reward-button">
                    Use
                  </button>
                </div>
              </div>

              <RewardRow points="30" reward="Choose a family game" />
              <RewardRow points="50" reward="Extra 20 minutes fun time" />
              <RewardRow points="100" reward="Special weekend reward" />
            </section>

            <section className="dark-card">
              <h2>Parent Settings</h2>
              <label>Weekly points goal</label>
              <input
                className="goal-input"
                type="number"
                min="1"
                value={data.weekGoal}
                onChange={(e) =>
                  setData({
                    ...data,
                    weekGoal: Number(e.target.value) || 1,
                  })
                }
              />
              <p>
                Tip: Use 5–10 points for simple tasks and 15–25 points for hard
                tasks.
              </p>
            </section>
          </aside>
        </div>
      </div>
    </div>
  );
}

function StatCard({ icon, label, value }) {
  return (
    <div className="stat-card">
      <div className="stat-icon">{icon}</div>
      <strong className="stat-value">{value}</strong>
      <span className="stat-label">{label}</span>
    </div>
  );
}

function MiniCard({ label, value }) {
  return (
    <div className="mini-card">
      <span>{label}</span>
      <strong>{value}</strong>
    </div>
  );
}

function ProgressCircle({ percent }) {
  return (
    <div className="circle-wrap">
      <div
        className="circle"
        style={{
          background: `conic-gradient(#4f46e5 ${
            percent * 3.6
          }deg, #e2e8f0 0deg)`,
        }}
      >
        <div className="circle-inner">
          <strong>{percent}%</strong>
          <span>Complete</span>
        </div>
      </div>
    </div>
  );
}

function LargeDailyCircle({ percent, done, total, label }) {
  return (
    <div className="big-circle-wrap">
      <div
        className="big-circle"
        style={{
          background: `conic-gradient(#4f46e5 ${
            percent * 3.6
          }deg, #dbe4ff 0deg)`,
        }}
      >
        <div className="big-circle-inner">
          <div className="big-percent">{percent}%</div>
          <div className="big-label">{label}</div>
          <div className="big-tasks">
            {done}/{total} tasks
          </div>
        </div>
      </div>
    </div>
  );
}

function ProgressBar({ label, value, detail }) {
  return (
    <div className="progress-bar-box">
      <div className="progress-bar-top">
        <strong>{label}</strong>
        <span>{detail}</span>
      </div>
      <div className="progress-track">
        <div className="progress-fill" style={{ width: `${value}%` }} />
      </div>
    </div>
  );
}

function RewardRow({ points, reward }) {
  return (
    <div className="reward-row">
      <span>{reward}</span>
      <strong>{points} pts</strong>
    </div>
  );
}
EOF
