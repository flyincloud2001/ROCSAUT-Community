# 後端 API 文件

## 基本資訊
- 初期後端：https://rocsaut-club-platform.vercel.app
- 所有 Community API 使用 /api/community/ 前綴
- 認證：Authorization: Bearer {jwt_token}
- 內容類型：application/json

## 認證 API

### POST /api/community/auth/token
取得 JWT Token
請求：{ "googleToken": "string" }
回傳：{ "token": "string", "user": User }

### POST /api/community/auth/invite
管理員邀請新用戶
請求：{ "email": "string", "role": "member" | "alumni" | "user" }
回傳：{ "success": true }

## 用戶 API

### GET /api/community/users/me
取得目前登入用戶資料
回傳：User

### PATCH /api/community/users/me
更新個人資料
請求：{ "displayName": "string", "bio": "string", "avatarUrl": "string" }
回傳：User

### GET /api/community/users/:id
取得指定用戶公開資料
回傳：User

### GET /api/community/users
取得成員目錄（需登入）
Query：?role=alumni&graduationYear=2022&page=1&limit=20
回傳：{ "users": User[], "total": number }

## 發文 API

### GET /api/community/posts
取得動態牆發文列表
Query：?category=&sort=hot|new|top&page=1&limit=20
回傳：{ "posts": Post[], "total": number }

### POST /api/community/posts
建立新發文
請求：{ "title": "string", "content": "string", "categoryId": "string", "anonymous": boolean, "images": string[] }
回傳：Post

### GET /api/community/posts/:id
取得單篇發文
回傳：Post

### PATCH /api/community/posts/:id
編輯發文（只有作者和管理員可操作）
請求：{ "title": "string", "content": "string" }
回傳：Post

### DELETE /api/community/posts/:id
刪除發文（只有作者和管理員可操作）
回傳：{ "success": true }

## 留言 API

### GET /api/community/posts/:id/comments
取得留言列表
回傳：{ "comments": Comment[] }

### POST /api/community/posts/:id/comments
新增留言
請求：{ "content": "string", "anonymous": boolean, "parentId": "string | null" }
回傳：Comment

### DELETE /api/community/posts/:id/comments/:commentId
刪除留言
回傳：{ "success": true }

### POST /api/community/posts/:id/comments/:commentId/best
標記最佳回覆（只有發文者可操作）
回傳：{ "success": true }

## 按讚 API

### POST /api/community/posts/:id/vote
對發文按讚或倒讚
請求：{ "type": "up" | "down" }
回傳：{ "upvotes": number, "downvotes": number }

### POST /api/community/comments/:id/vote
對留言按讚或倒讚
請求：{ "type": "up" | "down" }
回傳：{ "upvotes": number, "downvotes": number }

## 分類 API

### GET /api/community/categories
取得所有分類
回傳：{ "categories": Category[] }

## 搜尋 API

### GET /api/community/search
全站搜尋
Query：?q=關鍵字&type=posts|users&page=1&limit=20
回傳：{ "posts": Post[], "users": User[], "total": number }

## 通知 API

### GET /api/community/notifications
取得通知列表
回傳：{ "notifications": Notification[] }

### POST /api/community/notifications/read
標記所有通知為已讀
回傳：{ "success": true }

## 管理員 API

### GET /api/community/admin/users
取得所有用戶列表（管理員限定）
回傳：{ "users": User[] }

### PATCH /api/community/admin/users/:id
修改用戶身份標籤或停權（管理員限定）
請求：{ "role": "member" | "alumni" | "user" | "banned", "graduationYear": number }
回傳：User

### GET /api/community/admin/reward
取得當月 Instagram 獎勵排行（管理員限定）
回傳：{ "ranking": RewardRanking[] }

## 資料型別

### User
```
{
  id: string
  email: string
  displayName: string
  avatarUrl: string | null
  bio: string | null
  role: "member" | "alumni" | "user" | "admin"
  graduationYear: number | null
  level: 1 | 2 | 3 | 4 | 5
  points: number
  createdAt: string
}
```

### Post
```
{
  id: string
  title: string
  content: string
  images: string[]
  anonymous: boolean
  author: User | null
  categoryId: string
  upvotes: number
  downvotes: number
  commentCount: number
  createdAt: string
  updatedAt: string
}
```

### Comment
```
{
  id: string
  content: string
  anonymous: boolean
  author: User | null
  parentId: string | null
  upvotes: number
  downvotes: number
  isBest: boolean
  createdAt: string
}
```

### Category
```
{
  id: string
  name: string
  description: string
  postCount: number
}
```

### Notification
```
{
  id: string
  type: "comment" | "vote" | "best" | "mention" | "reward"
  read: boolean
  postId: string | null
  commentId: string | null
  createdAt: string
}
```

### RewardRanking
```
{
  user: User
  totalUpvotes: number
  rank: number
}
```
