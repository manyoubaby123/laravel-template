FORMAT: 1A

# Laravel template

# 认证授权 [/api]
认证授权

## 获取用户的角色权限 [GET /api/limits]


+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": {
                    "roles": {
                        "suadmin": "超级管理员"
                    },
                    "perms": {
                        "/qrlogin/*": "/qrlogin/*"
                    }
                },
                "errors": null,
                "code": 0
            }

## 用账号密码登录 [POST /api/login]


+ Request (application/json)
    + Body

            {
                "username": "demo",
                "password": "testpw"
            }

+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": {
                    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE2OC4xLjEwODo4MDc3L2FwaS9sb2dpbiIsImlhdCI6MTQ4OTU2MzEyOCwiZXhwIjoxNDg5NTY2NzI4LCJuYmYiOjE0ODk1NjMxMjgsImp0aSI6IlBwR3VyY2hqT2cyb3RhV3YiLCJzdWIiOjEsInVzZXIiOnsiaWQiOjF9fQ.8BdtuyTS9oOiEOIJNnwKvbLIDpJ2Rr8aWqp8FPYvl04",
                    "user": {
                        "name": "测试姓名",
                        "username": "demo"
                    }
                },
                "errors": null,
                "code": 0
            }

## 获取扫码登录信息 [GET /api/qrcode]


+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": {
                    "expires": "60",
                    "nonce": "HVaCH2KVNQrgvY5AxegKIcMPknCf6Qcs",
                    "url": "http://xxx.xxx/xx.x/"
                },
                "errors": null,
                "code": 0
            }

## 用二维码 nonce 登录 [POST /api/qrlogin]


+ Request (application/json)
    + Body

            {
                "nonce": "HVaCH2KVNQrgvY5AxegKIcMPknCf6Qcs"
            }

+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": null,
                "errors": {
                    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE2OC4xLjEwODo4MDc3L2FwaS9sb2dpbiIsImlhdCI6MTQ4OTU2MzEyOCwiZXhwIjoxNDg5NTY2NzI4LCJuYmYiOjE0ODk1NjMxMjgsImp0aSI6IlBwR3VyY2hqT2cyb3RhV3YiLCJzdWIiOjEsInVzZXIiOnsiaWQiOjF9fQ.8BdtuyTS9oOiEOIJNnwKvbLIDpJ2Rr8aWqp8FPYvl04",
                    "user": {
                        "name": "测试姓名",
                        "username": "demo"
                    }
                },
                "code": 0
            }

## 用微信授权返回的 code 登录（移动端） [POST /api/codelogin]


+ Request (application/json)
    + Body

            {
                "code": "fafdcfac7e502ed2d008c52bf46abc67"
            }

+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": {
                    "total": 150,
                    "per_page": 15,
                    "current_page": 1,
                    "last_page": 10,
                    "next_page_url": "http:\/\/...",
                    "prev_page_url": null,
                    "from": 1,
                    "to": 15,
                    "data": {
                        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE2OC4xLjEwODo4MDc3L2FwaS9sb2dpbiIsImlhdCI6MTQ4OTU2MzEyOCwiZXhwIjoxNDg5NTY2NzI4LCJuYmYiOjE0ODk1NjMxMjgsImp0aSI6IlBwR3VyY2hqT2cyb3RhV3YiLCJzdWIiOjEsInVzZXIiOnsiaWQiOjF9fQ.8BdtuyTS9oOiEOIJNnwKvbLIDpJ2Rr8aWqp8FPYvl04",
                        "user": {
                            "name": "测试姓名",
                            "username": "demo"
                        }
                    }
                },
                "errors": null,
                "code": 0
            }

## 确认扫码登录 [POST /api/confirmqrlogin]


+ Request (application/json)
    + Body

            {
                "nonce": "HVaCH2KVNQrgvY5AxegKIcMPknCf6Qcs",
                "login": true
            }

+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": {
                    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE2OC4xLjEwODo4MDc3L2FwaS9sb2dpbiIsImlhdCI6MTQ4OTU2MzEyOCwiZXhwIjoxNDg5NTY2NzI4LCJuYmYiOjE0ODk1NjMxMjgsImp0aSI6IlBwR3VyY2hqT2cyb3RhV3YiLCJzdWIiOjEsInVzZXIiOnsiaWQiOjF9fQ.8BdtuyTS9oOiEOIJNnwKvbLIDpJ2Rr8aWqp8FPYvl04",
                    "user": {
                        "name": "测试姓名",
                        "username": "demo"
                    }
                },
                "errors": null,
                "code": 0
            }

# 用户 [/api/users]
用户

## 从企业号同步用户 [POST /api/users/sync]


+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": null,
                "errors": null,
                "code": 0
            }

## 获取用户列表 [GET /api/users/list{?page}]


+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": {
                    "total": 150,
                    "per_page": 15,
                    "current_page": 1,
                    "last_page": 10,
                    "next_page_url": "http:\/\/...",
                    "prev_page_url": null,
                    "from": 1,
                    "to": 15,
                    "data": [
                        {
                            "created_at": "2017-03-14 20:42:26",
                            "departments": "{}",
                            "email": null,
                            "id": 1,
                            "info": "{}",
                            "mobile": "",
                            "name": "超级管理员",
                            "status": 0,
                            "updated_at": "2017-03-14 20:42:49",
                            "username": "suadmin"
                        }
                    ]
                },
                "errors": null,
                "code": 0
            }

## 给用户分配角色 [POST /api/users/attachroles]


+ Request (application/json)
    + Body

            {
                "username": "admin",
                "rolenames": [
                    "admin",
                    "user"
                ]
            }

+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": null,
                "errors": null,
                "code": 0
            }

## 获取所有的角色列表 [GET /api/users/allroles]


+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": [
                    {
                        "id": 1,
                        "name": "suadmin",
                        "display_name": "超级管理员",
                        "description": "suadmin",
                        "created_at": "2017-03-16 11:14:14",
                        "updated_at": "2017-03-16 11:14:14"
                    }
                ],
                "errors": null,
                "code": 0
            }

# 部门管理 [/api/departments]
部门管理

## 从企业号同步部门 [POST /api/departments/sync]


+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "..."
            }

## 列出部门列表 [GET /api/departments/departments{?page}]


+ Response 200 (application/json)
    + Body

            {
                "status": "ok|error",
                "message": "...",
                "data": {
                    "total": 150,
                    "per_page": 15,
                    "current_page": 1,
                    "last_page": 10,
                    "next_page_url": "http:\/\/...",
                    "prev_page_url": null,
                    "from": 1,
                    "to": 15,
                    "data": [
                        {
                            "created_at": "2017-03-14 20:42:26",
                            "departments": "{}",
                            "email": null,
                            "id": 1,
                            "info": "{}",
                            "mobile": "",
                            "name": "超级管理员",
                            "status": 0,
                            "updated_at": "2017-03-14 20:42:49",
                            "username": "suadmin"
                        }
                    ]
                },
                "errors": null,
                "code": 0
            }