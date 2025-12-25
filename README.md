# 📋 Zoho Projects Task Management Widget

> A simple and powerful widget to manage your Zoho Projects tasks directly from Zoho SalesIQ.


## ✨ Features

| Feature | Description |
|---------|-------------|
| 👁️ **View Tasks** | See all your assigned tasks in one place |
| ➕ **Create Tasks** | Quickly create new tasks with all details |
| ✏️ **Edit Tasks** | Modify task details, status, and priority |
| 🗑️ **Delete Tasks** | Remove tasks with confirmation safety |
| 💬 **Add Comments** | Comment on tasks and view history |
| 📊 **Status Dashboard** | Visual breakdown of task statuses |

---

## 🚀 Installation

### 📝 Step 1: Setup Zoho Connection

Create a connection in Zoho SalesIQ:

```
🔗 Name: zoho_projects_connection
🔧 Service: Zoho Projects
🔐 Scopes: ZohoProjects.projects.READ, ZohoProjects.tasks.ALL
```

### ⚙️ Step 2: Update Configuration

Edit all handler files and change these lines:

```javascript
portalId = "your_portal_id";      // 🔍 Find in Zoho Projects Settings
projectId = "your_project_id";    // 🔍 Find in your project URL
```

### 📦 Step 3: Add to Zoho SalesIQ

1. 🏠 Go to **Settings** → **Developers** → **Widgets**
2. ➕ Click **Create new Custom Widget**
3. 📄 Copy `Detail handler.txt` to **Detail Handler** section
4. ⚡ Copy `Action handler.txt` to **Action Handler** section
5. 📋 Copy form controller files to **Form Controller** section:
   - ✖️ `Form controller- closeDetails handler.txt`
   - 💬 `Form controller-submitComment handler.txt`
   - ➕ `Form controller-submitNewTask handler.txt`
6. 💾 **Save** and **Publish**

---

## 📖 Usage Guide

### 👁️ View Tasks
```
1. Open widget in Zoho SalesIQ
2. See all your assigned tasks
3. Click "👁️ View Details" for full information
```

### ➕ Create Task
```
1. Click "➕ Create Task" button
2. Fill in required fields:
   - 📝 Task Name
   - ⚡ Priority (High/Medium/Low)
   - 📅 Due Date (optional)
   - 📄 Description (optional)
3. Click Submit
```

### ✏️ Edit Task
```
1. Open task details
2. Click "✏️ Edit Task" button
3. Update any fields
4. Click "💾 Save Changes"
```

### 🗑️ Delete Task
```
1. Open task details
2. Click "🗑️ Delete Task" button
3. Type "DELETE" to confirm
4. Task is permanently removed
```

### 💬 Add Comment
```
1. Find task with "In Progress" status
2. Click "💬 Add Comment" button
3. Type your comment
4. Click "📤 Submit Comment"
```

---

## 📁 File Structure

```
zoho-projects-widget/
│
├── 📄 Action handler.txt
├── 📄 Detail handler.txt
├── 📋 Form controller- closeDetails handler.txt
├── 📋 Form controller-submitComment handler.txt
├── 📋 Form controller-submitNewTask handler.txt
└── 📖 README.md
```

### 📝 File Descriptions

| File | Icon | Purpose |
|------|------|---------|
| `Detail handler.txt` | 📄 | Displays task list and overview dashboard |
| `Action handler.txt` | ⚡ | Handles all button clicks and actions |
| `Form controller- closeDetails handler.txt` | ✖️ | Validates close details action |
| `Form controller-submitComment handler.txt` | 💬 | Validates comment submissions |
| `Form controller-submitNewTask handler.txt` | ➕ | Validates new task creation |

---

## 🔧 Configuration

### 🔍 Finding Your IDs

#### 📊 Portal ID:
1. Go to **Zoho Projects**
2. Click **Settings** → **Portal Info**
3. 📋 Copy your **Portal ID**

#### 📁 Project ID:
1. Open your project in **Zoho Projects**
2. 👀 Look at the URL: 
   ```
   https://projects.zoho.com/portal/[portalId]#projectid=[projectId]
   ```
3. 📋 Copy the **project ID** from the URL

### 🔐 Connection Setup

1. 🏠 Go to **Settings** → **Developers** → **Connections**
2. ➕ Click **"Add Connection"**
3. 🎯 Select **"Zoho Projects"**
4. ✍️ Name it: `zoho_projects_connection`
5. ✅ Grant permissions:
   - 📖 `ZohoProjects.projects.READ`
   - ✏️ `ZohoProjects.tasks.ALL`
6. 💾 **Save** the connection

---

## 🎨 UI Components

### 📊 Status Indicators
| Icon | Status | Description |
|------|--------|-------------|
| 📂 | **Open** | New or pending tasks |
| 🔄 | **In Progress** | Currently being worked on |
| ✅ | **Completed** | Finished tasks |

### ⚡ Priority Levels
| Icon | Priority | Use Case |
|------|----------|----------|
| 🔴 | **High** | Urgent, time-sensitive tasks |
| 🟡 | **Medium** | Standard priority tasks |
| 🟢 | **Low** | Non-urgent tasks |

### 🎯 Action Buttons
| Button | Icon | Function |
|--------|------|----------|
| View Details | 👁️ | Opens detailed task view |
| Edit Task | ✏️ | Modify task information |
| Delete Task | 🗑️ | Remove task (with confirmation) |
| Add Comment | 💬 | Add note to task |
| Create Task | ➕ | Create new task |

---

## 🐛 Troubleshooting

### ❌ Tasks not showing?
- ✅ Check your `portalId` and `projectId` are correct
- ✅ Verify connection is active in SalesIQ
- ✅ Ensure tasks are assigned to your email
- ✅ Check API permissions are granted

### ❌ Can't edit or delete?
- ✅ Verify API connection has write permissions
- ✅ Check `ZohoProjects.tasks.ALL` scope is enabled
- ✅ Ensure you're the task owner
- ✅ Check connection is not expired

### ❌ Form validation errors?
- ✅ Ensure all required fields are filled
- ✅ Check date format is correct (MM-DD-YYYY)
- ✅ Verify task name is under 255 characters
- ✅ Confirm user selection is valid

### ❌ Form controller not working?
- ✅ Make sure all three form controller files are uploaded
- ✅ Check each file is in the correct Form Controller section
- ✅ Verify form names match in all files
- ✅ Test each form individually

### ❌ Connection issues?
- ✅ Re-authenticate the Zoho Projects connection
- ✅ Check if API limits are reached
- ✅ Verify network connectivity
- ✅ Review SalesIQ developer console logs

---

## 📊 API Endpoints Used

| Endpoint | Method | Purpose | Icon |
|----------|--------|---------|------|
| `/tasks/` | GET | Fetch all tasks | 📥 |
| `/tasks/{id}/` | GET | Get task details | 🔍 |
| `/tasks/` | POST | Create new task | ➕ |
| `/tasks/{id}/` | POST | Update task | ✏️ |
| `/tasks/{id}/` | DELETE | Delete task | 🗑️ |
| `/tasks/{id}/comments/` | GET | Fetch comments | 💬 |
| `/tasks/{id}/comments/` | POST | Add comment | 📤 |
| `/projects/{id}/users/` | GET | Get team members | 👥 |

---

## 🎯 Roadmap

### 🚧 Planned Features

- [ ] 🔍 **Search** - Search tasks by name or description
- [ ] 🎛️ **Filter** - Filter by status, priority, or due date
- [ ] 📈 **Sort** - Sort by priority, due date, or creation date
- [ ] 🎨 **Dark Mode** - Toggle dark/light theme
- [ ] 📱 **Mobile View** - Optimized mobile interface
- [ ] 📎 **Attachments** - Upload and view file attachments
- [ ] ⏱️ **Time Tracking** - Log time spent on tasks
- [ ] 🔔 **Notifications** - Alert for upcoming deadlines
- [ ] 📤 **Export** - Export task list to CSV/Excel
- [ ] 🔗 **Dependencies** - View task dependencies

