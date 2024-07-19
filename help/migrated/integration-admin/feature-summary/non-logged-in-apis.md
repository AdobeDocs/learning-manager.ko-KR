---
description: 헤드리스 인터페이스 개발을 위한 임시 방문 API에 대해 알아보십시오.
jcr-language: en_us
title: 로그인하지 않은 API
source-git-commit: 21e2a4a5e73fcbddb64e0afec0a896b315e38688
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# 로그인하지 않은 API

이 문서에서 헤드리스 또는 임시 방문 환경에 대한 데이터를 제공하는 Adobe Learning Manager API에 대해 자세히 알아보십시오.
공개 검색 API

## 공개 검색 API

### 공용 ES를 사용하여 데이터 필터링

공개 검색 API를 사용하면 기본 검색 API와 함께 사용하여 강의를 필터링할 수 있는 필터 데이터를 가져올 수 있습니다. 이 API는 검색 API에서 사용할 수 있는 모든 필터를 제공합니다.

**샘플 컬**

GET 메서드를 사용하여 다음과 같이 요청합니다. 아래 curl 명령에서 &lt;Base_URL>을 기본 URL로 대체합니다. 교육 데이터 액세스 커넥터 페이지에서 &lt;Base_URL>을 찾을 수 있습니다.

```
curl --location '<Base_URL>/filterableData'
```

**샘플 응답**

```
{
    "terms": {
        "loSkillLevels": [
            "1"
        ],
        "catalogNames": [
            "Default Catalog"
        ],
"catalogLabelIds": [
            "0000_1111"
        ],
        "loType": [
            "course"
        ],
        "availability": [
            "waitlistAvailable",
            "seatAvailable"
        ],
        "loSkillNames": [
            "General"
        ],
        "tags": [
            "course_tag"
        ],
        "authors": [
            "author_1"        
]
    },
    "range": {
        "duration": [
            "0"
        ],
        "dateCreated": [
            "2024-06-13T04:32:17.000Z"
        ],
        "price": [
            "0.0"
        ],
        "sessionEndTime": [
            "2024-06-18T20:30:00.000Z"
        ],
        "averageRating": [
            "0.0"
        ],
        "sessionStartTime": [
            "2024-06-18T19:30:00.000Z"
        ],
        "publishDate": [
            "2024-06-13T04:32:51.000Z"
        ],
        "ratingsCount": [
            "0"
        ]
    },
    "term": {}
}
```

**필터 옵션**

| 옵션 | 설명 |
| --- | --- |
| `loSkillLevels` | 강의에 등록하는 데 필요한 숙련도 수준입니다. |
| `catalogNames` | 사용 가능한 카탈로그 이름 목록입니다. |
| `loType` | 사용 가능한 학습 객체 유형 |
| `availability` | 좌석 예약 가능 여부 및 대기자 명단 예약 가능 여부. |
| `loSkillNames` | 학습 객체에 추가된 스킬 이름 |
| `tags` | 학습 객체와 연관된 태그입니다. |
| `authors` | 학습 객체의 작성자 이름 |
| `duration` | 학습 객체의 지속 기간입니다. |
| `dateCreated` | 학습 객체가 생성된 날짜입니다. |
| `sessionEndTime` | 세션이 종료된 시간입니다. |
| `averageRating` | 학습 개체의 평균 평가 등급입니다. |
| `sessionStartTime` | 세션이 시작된 시간입니다. |
| `publishDate` | 학습 개체의 게시 날짜입니다. |
| `ratingsCount` | 학습 개체의 등급 수 |

### API 검색

공개 검색 API를 사용하면 제공된 데이터를 사용하여 기본 검색 데이터를 가져올 수 있습니다.

**샘플 컬**

POST 방법을 사용하여 다음과 같은 요청을 하십시오. 아래 curl 명령에서 &lt;Base_URL>을 기본 URL로 대체합니다. 교육 데이터 액세스 커넥터 페이지에서 &lt;Base_URL>을 찾을 수 있습니다.

```
curl --location '<Base_URL>/search?size=1000' \
--header 'content-type: application/json' 

--data '{
   "query": "",
   
    "sort": {
        "name": "publishDate",
        "order": "desc"
    },
    "lang": [
        "en-US"
    ],
    "filters": {
        "terms": {
            "loType": [
                "course",
                "learningProgram",
                "certification"
            ],
            "availability": [
                "seatAvailable",
                "waitlistAvailable"
            ]
        },
        "term": {
            "enrollmentDeadlinePassed": "true"
        },
        "range": {
                "dateCreated": [
                    {
                        "gte": "2024-05-02T02:48:51.000Z"
                    }
                ],
            "sessionStartTime": [
                {
                   "gte": "2024-06-18T19:30:00.000Z"
                }
            ],
            "sessionEndTime": [
                {
                   "lte": "2024-06-20T09:30:00.000Z"     
                }
            ]
        }
    }
}'
```

**API 호출의 샘플 응답**

```
{
    "results": [
        {
            "loId": "course:11332313",
            "loType": "course",
            "tags": [
                "course_tag"
            ],
            "authors": [
                "author1",
                "author2"
            ],
            "status": "Published",
            "duration": 0,
            "publishDate": "2024-06-13T04:32:51.000Z",
            "dateCreated": "2024-06-13T04:32:17.000Z",
            "name": "vc coursse to check ",
            "averageRating": 0.0,
            "ratingsCount": 0,
            "loSkillNames": [
                "General"
            ],
            "loSkillLevels": [
                "1"
            ],
            "loInstances": [
                {
                    "id": "14346696",
                    "name": "Default Instance",
                    "status": "Active",
                    "price": 0.0
                }
            ],
            "catalogInfo": [
                {
                    "id": "37779",
                    "name": "Default Catalog"
                }
            ]
        }
    ],
    "request": {
        "query": "",
        "filters": {
            "terms": {
                "loType": [
                    "course",
                    "learningProgram",
                    "certification"
                ],
                "loSkillNames": [
                    "General"
                ],
                "deliveryType": [],
                "availability": [
                    "seatAvailable",
                    "waitlistAvailable"
                ]
            },
            "term": {
                "enrollmentDeadlinePassed": "true"
            },
            "range": {
                "dateCreated": [
                    {
                        "gte": "2024-05-02T02:48:51.000Z"
                    }
                ],
                "sessionStartTime": [
                    {
                        "gte": "2024-06-18T19:30:00.000Z"
                    }
                ],
                "sessionEndTime": [
                    {
                        "lte": "2024-06-20T09:30:00.000Z"
                    }
                ]
            }
        },
        "sort": {
            "name": "publishDate",
            "order": "desc"
        },
        "lang": [
            "en-US"
        ]
    },
    "self": "<Base_URL>/search?page=0&size=1000",
    "count": 1
}
```

**검색 API의 정렬 옵션**

결과에 적용할 다음 정렬 옵션을 선택할 수 있습니다.

| 옵션 | 설명 |
| --- | --- |
| `duration` | 학습 개체의 기간입니다. |
| `publishDate` | 학습 개체의 게시 날짜입니다. |
| `dateCreated` | 학습 객체가 생성된 날짜입니다. |
| `name_en` | 학습 개체의 이름입니다. |
| `averageRating` | 학습자가 제공한 평균 평가 등급입니다. |
| `ratingsCount` | 학습 개체의 등급 수 |
| `relevance(default)` | 관련 데이터는 검색 키워드에 기반합니다. |

### 공개 검색 API를 사용하여 학습 개체 데이터 가져오기

공개 ES 학습 객체 API를 사용하면 헤드리스 인터페이스에서 사용 가능한 학습 객체의 유형 및 ID 목록을 가져올 수 있습니다.

**샘플 컬**

GET 메서드를 사용하여 다음과 같이 요청합니다. 아래 curl 명령에서 &lt;Base_URL>을 기본 URL로 대체합니다. 교육 데이터 액세스 커넥터 페이지에서 &lt;Base_URL>을 찾을 수 있습니다.

```
curl --location '<Base_URL>/learningObjectIds'
```

**API 호출에 대한 샘플 응답**

```
{
    "loIds": [
        "course:1132800",
"certification:126009",
"learningProgram:104433"
    ]
}
```

## 강의 요약 API

강의 요약 API를 사용하면 특정 강의에 대한 세부 정보를 검색할 수 있습니다.

**샘플 컬**

GET 메서드를 사용하여 다음과 같이 요청합니다. 아래 curl 명령에서 &lt;Base_URL>을 기본 URL로 대체합니다. 교육 데이터 액세스 커넥터 페이지에서 &lt;Base_URL>을 찾을 수 있습니다. &lt;Course_ID>를 특정 과정 ID로 바꿉니다.

```
curl --location '<Base_URL>/loSummary?loId=course%3A<Course_ID>'
```

**API 호출의 샘플 응답**

```
{
    "results": [
        {
            "instanceId": "14336686",
            "courseId": "11312313",
            "accountId": "44355",
            "seatConsumed": 1,
            "seatLimit": 1,
            "waitlistLimit":1,
            "waitlistCount": 1,
            "seatAvailable": false,
            "waitlistAvailable": false
        }
    ],
    "count": 1
}
```

>[!NOTE]
>
>강의에 여러 인스턴스가 있는 경우, 모든 인스턴스에 대한 세부 정보를 확인할 수 있습니다.

## 강의 세부 정보를 위한 CDN JSON API

CDN JSON API를 사용하면 특정 강의에 대한 전체 강의 정보를 검색할 수 있습니다.

**강의에 대한 샘플 컬**

GET 메서드를 사용하여 다음과 같이 요청합니다. 아래 curl 명령에서 &lt;CDN_path>를 기본 URL로 대체합니다. 교육 데이터 액세스 커넥터 페이지에서 &lt;CDN_path>를 찾을 수 있습니다. &lt;Course_ID>를 특정 과정 ID로 바꿉니다.

```
curl --location '<CDN_path_URL>/course/<Course_ID>.json'
```

**학습 경로 및 인증에 대한 샘플 컬**

```
curl --location '<CDN_path_URL>/learningProgram/<LearningProgram_ID>.json'
```

```
curl --location '<CDN_path_URL>/ certification /<Certification_ID>.json'
```

**API 호출의 샘플 응답**

```
{
    "data": {
        "id": "course:11342313",
        "type": "learningObject",
        "attributes": {
            "authorNames": [
                "author1",
                "author2"
            ],
            "dateCreated": "2024-06-13T04:32:17.000Z",
            "datePublished": "2024-06-13T04:32:51.000Z",
            "dateUpdated": "2024-06-13T04:32:51.000Z",
            "duration": 0,
            "effectiveModifiedDate": "2024-06-13T04:32:51.000Z",
            "effectivenessIndex": 0,
            "enrollmentType": "Self Enroll",
            "hasOptionalLoResources": false,
            "hasPreview": false,
            "isExternal": false,
            "isMqaEnabled": false,
            "isPrerequisiteEnforced": false,
            "isSubLoOrderEnforced": false,
            "loResourceCompletionCount": 1,
            "loType": "course",
            "moduleResetEnabled": false,
            "state": "Published",
            "tags": [
                "course_tag"
            ],
            "unenrollmentAllowed": true,
            "localizedMetadata": [
                {
                    "description": "",
                    "locale": "en-US",
                    "name": "vc coursse to check "
                }
            ],
            "rating": {
                "averageRating": 0,
                "ratingsCount": 0
            }
        },
        "relationships": {
            "authors": {
                "data": [
                    {
                        "id": "13138897",
                        "type": "user"
                    }
                ]
            },
            "instances": {
                "data": [
                    {
                        "id": "course:11332313_14336696",
                        "type": "learningObjectInstance"
                    }
                ]
            },
            "skills": {
                "data": [
                    {
                        "id": "course:11332313_237719",
                        "type": "learningObjectSkill"
                    }
                ]
            }
        }
    },
    "included": [
        {
            "id": "237719",
            "type": "skill",
            "attributes": {
                "name": "General",
                "state": "Active"
            },
            "relationships": {
                "levels": {
                    "data": [
                        {
                            "id": "237719_1",
                            "type": "skillLevel"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313",
            "type": "learningObject",
            "attributes": {
                "authorNames": [
                    "m 41",
                    "rae"
                ],
                "dateCreated": "2024-06-13T04:32:17.000Z",
                "datePublished": "2024-06-13T04:32:51.000Z",
                "dateUpdated": "2024-06-13T04:32:51.000Z",
                "duration": 0,
                "effectiveModifiedDate": "2024-06-13T04:32:51.000Z",
                "effectivenessIndex": 0,
                "enrollmentType": "Self Enroll",
                "hasOptionalLoResources": false,
                "hasPreview": false,
                "isExternal": false,
                "isMqaEnabled": false,
                "isPrerequisiteEnforced": false,
                "isSubLoOrderEnforced": false,
                "loResourceCompletionCount": 1,
                "loType": "course",
                "moduleResetEnabled": false,
                "state": "Published",
                "tags": [
                    "course_tag"
                ],
                "unenrollmentAllowed": true,
                "localizedMetadata": [
                    {
                        "description": "",
                        "locale": "en-US",
                        "name": "course name "
                    }
                ],
                "rating": {
                    "averageRating": 0,
                    "ratingsCount": 0
                }
            },
            "relationships": {
                "authors": {
                    "data": [
                        {
                            "id": "13128897",
                            "type": "user"
                        }
                    ]
                },
                "instances": {
                    "data": [
                        {
                            "id": "course:11312313_14336696",
                            "type": "learningObjectInstance"
                        }
                    ]
                },
                "skills": {
                    "data": [
                        {
                            "id": "course:11312313_237719",
                            "type": "learningObjectSkill"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313_14336696_12034506_0",
            "type": "learningObjectResource",
            "attributes": {
                "externalReporting": false,
                "isExpiredSubmission": false,
                "loResourceType": "Content",
                "multipleAttemptEnabled": false,
                "previewEnabled": false,
                "resourceType": "Virtual Classroom",
                "submissionEnabled": false,
                "localizedMetadata": [
                    {
                        "description": "",
                        "locale": "en-US",
                        "name": "vc session"
                    }
                ]
            },
            "relationships": {
                "learningObject": {
                    "data": {
                        "id": "course:11312313",
                        "type": "learningObject"
                    }
                },
                "resources": {
                    "data": [
                        {
                            "id": "course:11312313_14336696_12034506_0_resource",
                            "type": "resource"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313_237719",
            "type": "learningObjectSkill",
            "attributes": {
                "credits": 1,
                "learningObjectId": "course:11312313"
            },
            "relationships": {
                "skillLevel": {
                    "data": {
                        "id": "237719_1",
                        "type": "skillLevel"
                    }
                }
            }
        },
        {
            "id": "13128897",
            "type": "user",
            "attributes": {
                "avatarUrl": "https://abccontents.adobe.com/public/images/default_user_avatar.svg",
                "binUserId": "1f8c01aa-7f58-42e9-bc40-11537eb6498d",
                "email": "manjusha+41re@adobetest.com",
                "enrollOnClick": false,
                "gamificationEnabled": true,
                "lastLoginDate": "2024-06-13T04:23:45.000Z",
                "name": "m 41",
                "pointsEarned": 0,
                "pointsRedeemed": 0,
                "preferredResolution": "AUTO",
                "profile": "admin",
                "roles": [
                    "Learner",
                    "Admin",
                    "Author",
                    "Instructor",
                    "Integration Admin"
                ],
                "state": "ACTIVE",
                "userType": "Internal"
            },
            "relationships": {
                "account": {
                    "data": {
                        "id": "44355",
                        "type": "account"
                    }
                }
            }
        },
        {
            "id": "course:11312313_14336696_12034506_0_resource",
            "type": "resource",
            "attributes": {
                "avatarUrls": [
                    "https://abccontents.adobe.com/public/images/default_user_avatar.svg"
                ],
                "completionDeadline": "2024-06-18T20:30:00.000Z",
                "contentType": "Virtual Classroom",
                "dateStart": "2024-06-18T19:30:00.000Z",
                "desiredDuration": 3600,
                "hasQuiz": false,
                "hasToc": false,
                "instructorNames": [
                    "instructor1"
                ],
                "isDefault": true,
                "locale": "en-US",
                "location": "http://google.com",
                "name": "vc session",
                "onlyQuiz": false,
                "reportingType": "NONE"
            }
        },
        {
            "id": "course:11312313_14336696",
            "type": "learningObjectInstance",
            "attributes": {
                "dateCreated": "2024-06-13T04:32:18.000Z",
                "isDefault": true,
                "isFlexible": false,
                "state": "Active",
                "localizedMetadata": [
                    {
                        "locale": "en-US",
                        "name": "Default Instance"
                    }
                ],
                "seatConsumed": 0,
                "waitlistCount": 0
            },
            "relationships": {
                "learningObject": {
                    "data": {
                        "id": "course:11312313",
                        "type": "learningObject"
                    }
                },
                "loResources": {
                    "data": [
                        {
                            "id": "course:11312313_14336696_12034506_0",
                            "type": "learningObjectResource"
                        }
                    ]
                }
            }
        },
        {
            "id": "237719_1",
            "type": "skillLevel",
            "attributes": {
                "level": "1",
                "maxCredits": 1,
                "name": "Level 1"
            },
            "relationships": {
                "skill": {
                    "data": {
                        "id": "237719",
                        "type": "skill"
                    }
                }
            }
        }
    ]
}
```
