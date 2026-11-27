# MongoDB Atlas - Browse Collections Structure

## Database Name: `projectmanagement`

When you browse collections in MongoDB Atlas, you will see these 5 collections:

---

## 1. **users** Collection

**Sample Document:**
```json
{
  "_id": "ObjectId('...')",
  "name": "Alex Johnson",
  "email": "admin@test.com",
  "password": "$2a$10$hashed_password_here",
  "role": "admin",
  "department": "Management",
  "phone": "+1-555-0101",
  "isActive": true,
  "avatar": "",
  "lastLogin": "2024-03-15T10:30:00.000Z",
  "createdAt": "2024-01-01T00:00:00.000Z",
  "updatedAt": "2024-03-15T10:30:00.000Z"
}
```

**Total Documents:** 8 users
- 1 Admin
- 1 Manager  
- 6 Team Members

---

## 2. **projects** Collection

**Sample Document:**
```json
{
  "_id": "ObjectId('...')",
  "name": "Customer Portal Redesign",
  "description": "Complete overhaul of the customer-facing portal with modern UI/UX...",
  "status": "in-progress",
  "priority": "high",
  "startDate": "2024-01-15T00:00:00.000Z",
  "endDate": "2024-06-30T00:00:00.000Z",
  "owner": "ObjectId('user_id')",
  "members": [
    "ObjectId('user_id_1')",
    "ObjectId('user_id_2')",
    "ObjectId('user_id_3')"
  ],
  "progress": 68,
  "budget": 150000,
  "color": "#2563eb",
  "createdAt": "2024-01-15T00:00:00.000Z",
  "updatedAt": "2024-03-15T00:00:00.000Z"
}
```

**Total Documents:** 8 projects
- Customer Portal Redesign (68% complete)
- Mobile App Development (45% complete)
- Marketing Campaign Q2 (55% complete)
- Data Analytics Dashboard (0% - not started)
- API Integration Platform (72% complete)
- Security Audit & Compliance (85% complete)
- Employee Training Portal (0% - not started)
- Cloud Migration Initiative (38% complete)

---

## 3. **tasks** Collection

**Sample Document:**
```json
{
  "_id": "ObjectId('...')",
  "title": "Design new homepage layout",
  "description": "Create wireframes and high-fidelity mockups for the new homepage...",
  "status": "completed",
  "priority": "high",
  "project": "ObjectId('project_id')",
  "assignedTo": "ObjectId('user_id')",
  "createdBy": "ObjectId('user_id')",
  "dueDate": "2024-02-28T00:00:00.000Z",
  "tags": ["design", "ui", "homepage"],
  "comments": [
    {
      "user": "ObjectId('user_id')",
      "text": "Great work on the initial designs!",
      "createdAt": "2024-02-20T00:00:00.000Z",
      "_id": "ObjectId('...')"
    }
  ],
  "attachments": [],
  "createdAt": "2024-02-01T00:00:00.000Z",
  "updatedAt": "2024-02-28T00:00:00.000Z"
}
```

**Total Documents:** 25 tasks
- Status breakdown:
  - To Do: 5 tasks
  - In Progress: 10 tasks
  - Review: 4 tasks
  - Completed: 6 tasks

---

## 4. **notifications** Collection

**Sample Document:**
```json
{
  "_id": "ObjectId('...')",
  "user": "ObjectId('user_id')",
  "title": "New Task Assigned",
  "message": "You have been assigned to task: Performance optimization",
  "type": "task",
  "isRead": false,
  "link": "/tasks",
  "createdAt": "2024-03-15T10:00:00.000Z",
  "updatedAt": "2024-03-15T10:00:00.000Z"
}
```

**Total Documents:** 5 notifications
- Types: task, deadline, mention, project, system

---

## 5. **activities** Collection

**Sample Document:**
```json
{
  "_id": "ObjectId('...')",
  "user": "ObjectId('user_id')",
  "action": "created",
  "entity": "project",
  "entityId": "ObjectId('project_id')",
  "description": "Created project: Customer Portal Redesign",
  "createdAt": "2024-03-15T09:00:00.000Z",
  "updatedAt": "2024-03-15T09:00:00.000Z"
}
```

**Total Documents:** 5 activities
- Actions: created, updated, completed, deleted

---

## How to View in MongoDB Atlas

1. **Login to MongoDB Atlas:** https://cloud.mongodb.com/
2. **Click "Database"** in left sidebar
3. **Click "Browse Collections"** on your cluster
4. **Select Database:** `projectmanagement`
5. **You'll see 5 collections:**
   - users (8 documents)
   - projects (8 documents)
   - tasks (25 documents)
   - notifications (5 documents)
   - activities (5 documents)

6. **Click any collection** to see the documents inside
7. **Click any document** to see full details

---

## Visual Structure in MongoDB Atlas

```
📁 projectmanagement (Database)
  ├── 📄 users (8 documents)
  │   ├── Alex Johnson (Admin)
  │   ├── Sarah Williams (Manager)
  │   ├── Michael Chen (Frontend Dev)
  │   ├── Emily Rodriguez (UI/UX Designer)
  │   ├── David Kim (Backend Dev)
  │   ├── Jessica Martinez (QA)
  │   ├── Robert Taylor (DevOps)
  │   └── Lisa Anderson (Marketing)
  │
  ├── 📄 projects (8 documents)
  │   ├── Customer Portal Redesign
  │   ├── Mobile App Development
  │   ├── Marketing Campaign Q2
  │   ├── Data Analytics Dashboard
  │   ├── API Integration Platform
  │   ├── Security Audit & Compliance
  │   ├── Employee Training Portal
  │   └── Cloud Migration Initiative
  │
  ├── 📄 tasks (25 documents)
  │   ├── Design new homepage layout
  │   ├── Implement responsive navigation
  │   ├── Integrate payment gateway
  │   ├── User authentication system
  │   ├── Performance optimization
  │   └── ... (20 more tasks)
  │
  ├── 📄 notifications (5 documents)
  │   ├── New Task Assigned
  │   ├── Task Due Soon
  │   ├── Comment on Your Task
  │   └── ... (2 more)
  │
  └── 📄 activities (5 documents)
      ├── Created project: Customer Portal Redesign
      ├── Completed task: Implement responsive navigation
      └── ... (3 more)
```

---

## Data Relationships

**Projects → Users:**
- Each project has an `owner` (User ID)
- Each project has `members` array (User IDs)

**Tasks → Projects:**
- Each task belongs to a `project` (Project ID)

**Tasks → Users:**
- Each task has `assignedTo` (User ID)
- Each task has `createdBy` (User ID)

**Notifications → Users:**
- Each notification belongs to a `user` (User ID)

**Activities → Users:**
- Each activity is performed by a `user` (User ID)

---

## Total Data Summary

When you browse collections, you'll see:

| Collection      | Documents | Description                           |
|-----------------|-----------|---------------------------------------|
| users           | 8         | Team members with roles               |
| projects        | 8         | Active projects with progress         |
| tasks           | 25        | Tasks across all projects             |
| notifications   | 5         | User notifications                    |
| activities      | 5         | Recent activity logs                  |
| **TOTAL**       | **51**    | **Total documents in database**       |

---

## After Running Seed Script

Once you connect to MongoDB Atlas and run `npm run seed`, all this data will be visible in your MongoDB Atlas dashboard under:

**Database → Browse Collections → projectmanagement**

You can then:
- ✅ View all documents
- ✅ Edit documents manually
- ✅ Delete documents
- ✅ Add new documents
- ✅ Export data
- ✅ Create indexes
- ✅ Monitor queries

---

**This is exactly what you'll see when you browse the `projectmanagement` database in MongoDB Atlas!** 🎯
