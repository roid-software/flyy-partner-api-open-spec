# <ins>Api: Flyy Partner</ins>

## name: <ins>Get Wallet Types</ins>

desc: Get the list of available wallet types

method: **"GET"**

url: *"/v1/{{partner-id}}/wallet_types"*

example : /v1/12345bef00abc/wallet_types

case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "collection",
                "count": 15,
                "items": [
                    {
                        "id": 21,
                        "is_active": false,
                        "entity": "wallet_type",
                        "name": "Cash"
                    },
                    {
                        "id": 22,
                        "is_active": true,
                        "entity": "wallet_type",
                        "name": "Coins"
                    },
                  ]
                },



## name: <ins>Get credit statement for the specified wallet type</ins>

desc: Get credit statement for the specified wallet type

method: **"GET"**

url: *"/v1/{{partner-id}}/user/{{ext-user-id}}/wallet/{{wallet-type-id}}/credits*

example : /v1/12345bef00abc/user/777/wallet/8055/credits?page=1&per_page=10

    query-params :
                    key: page        value: 1
                    key: per_page    value: 10

case:

success: **true**

    o/p: {
        "success": true,
        "response_code": 200,
        "entity": "collection",
        "total_sum": 0,
        "count": 0,
        "items": []
    }

success: **false**

    {
        "success": false,
        "response_code": 422,
        "error": {
            "code": "INVALID_DATA",
            "description": "Invalid Wallet Type.",
            "invalid_fields": [
                "wallet_type_id"
            ]
        }
    }



## name: <ins>Get debit statement for the specified wallet type</ins>

desc: Get debit statement for the specified wallet type

method: **"GET"**

url: *"/v1/{{partner-id}}/user/{{ext-user-id}}/wallet/{{wallet-type-id}}/debits*

example : /v1/12345bef00abc/user/777/wallet/8055/debits?page=1&per_page=10

    query-params :
                    key: page        value: 1
                    key: per_page    value: 10

case:

success: **true**

    o/p: {
        "success": true,
        "response_code": 200,
        "entity": "collection",
        "total_sum": 0,
        "count": 0,
        "items": []
    }

success: **false**

    {
        "success": false,
        "response_code": 422,
        "error": {
            "code": "INVALID_DATA",
            "description": "Invalid Wallet Type.",
            "invalid_fields": [
                "wallet_type_id"
            ]
        }
    }





## name: <ins>Get wallet balance of a user in the specified wallet type</ins>

desc: Get wallet balance of a user in the specified wallet type

method: **"GET"**

url: *"v1/{{partner-id}}/user/{{ext-user-id}}/wallet/{{wallet-type-id}}*

example : /v1/12345bef00abc/user/777/wallet/8055/100

    query-params :
                    key: page        value: 1
                    key: per_page    value: 10

case:

success: **true**

    o/p: {
        "success": true,
        "response_code": 200,
        "entity": "wallet",
        "wallet_type_id": 21,
        "balance": 0,
        "ext_user_id": "7828011085",
        "last_balance_updated": 1695340816,
        "last_credit": 1680523040,
        "last_debit": 1695340816
    }

success: **false**

    {
        "success": false,
        "response_code": 422,
        "error": {
            "code": "INVALID_DATA",
            "description": "Invalid Wallet Type.",
            "invalid_fields": [
                "wallet_type_id"
            ]
        }
    }



## name: <ins>Create a Stage User</ins>

desc: Create a new Stage User 

method: **"POST"**

url: *"v1/{{partner-id}}/stage-user

example : /v1/12345bef00abc/stage-user

    body :
             {"ext_user_id" : "{{ext-user-id}}"}

case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "user",
                "ext_user_id": "1133",
                "created_at": 1710743467
            }

success: **false**

            {
                "success": false,
                "message": "Ext uid has already been taken"
            }


## name: <ins>User Token API</ins>

desc: Use this request to get ext_user_token to be used for initializing the Web SDK

method: **"POST"**

url: *"/v1/{partner-id}/user/{ext-user-id}/user_token"*

example : /v1/12345bef00abc/user/123/user_token

          body: {"is_new": true, "username": "Test"}

case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "user_token",
                "ext_user_id": "{{ext-user-id}}",
                "token": "X6LJJDOTyy",
                "device_id": "74e539df-48f3-489a-b8e3-07a253a163e1"
            }

success: **false**

              o/p: {
                                 "success": false,
                                  "response_code": 422,
                                  "error": {
                                      "code": "INVALID_DATA",
                                      "description": "Invalid Ext User Id.",
                                      "invalid_fields": [
                                          "ext_user_id"
                                      ]
                                  }
                              }



## name: <ins>Get Segment List</ins>

desc: This gets the list of segments in your account and returns in array of segments

method: **"GET"**

url: *"/v1/{partner-id}/get_segments"*

example : /v1/12345bef00abc/get_segments

case:

success: **true**

                o/p: {
                    "success": true,
                    "response_code": 200,
                    "entity": "collection",
                    "count": 71,
                    "items": [
                        {
                            "id": 15558,
                            "key": "ti33333",
                            "title": "Ti33333"
                        },
                        {
                            "id": 15557,
                            "key": "title3333333",
                            "title": "Test333"
                        },
                        ]
                }



## name: <ins>Update Segment Title</ins>

desc: Validate User's Device Uniqueness

method: **"PUT"**

url: *"/v1/{partner-id}/segments/{segment_id}"*

example : /v1/12345bef00abc/segments/100

        body: {
            "segment_title": "New Title"
        }

case:

success: **true**

        o/p: {
            "success": true,
            "response_code": 200,
            "entity": "segment",
            "description": "Segment Updated",
            "segment": {
                "id": 3404,
                "key": "test_segement",
                "title": "New Title"
            }
        }

success: **false**

          o/p: {
              "success": false,
              "response_code": 422,
              "error": {
                  "code": "INVALID_DATA",
                  "description": "Invalid Segment Id"
              }
          }



## name: <ins>Add a user to a segment</ins>

desc: This API adds the user with ext-user-id to the segment specified by segment_key. If the segment is not present then a new Segment is created.

method: **"POST"**

url: *"/v1/{partner-id}/user/{ext-user-id}/add_segment"*

example : /v1/12345bef00abc/user/123/add_segment

            body: {
                  "segment_title": "Test",
                  "segment_key": "title"
                  }

case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "user_segment",
                "ext_user_id": "123",
                "segment_title": "Test",
                "segment_key": "title",
                "created_at": 1708088202
            }

success: **false**

          o/p: {
              "success": false,
              "response_code": 422,
              "error": {
                  "code": "PARAMETERS_MISSING",
                  "description": "Missing segment_key",
                  "missing_fields": [
                      "segment_key"
                  ]
              }
          }




## name: <ins>Remove User from a Segment</ins>

desc: This API will Remove the User from a specified Segment

method: **"POST"**

url: *"/v1/{partner-id}/user/{ext-user-id}/remove_segment"*

example : /v1/12345bef00abc/user/123/remove_segment

              body: {
              "segment_key": "title"
              }

case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "user_segment",
                "description": "User removed from the Segment"
            }

success: **false**

                o/p: {
                    "success": false,
                    "response_code": 422,
                    "error": {
                        "code": "INVALID_DATA",
                        "description": "Invalid Segment Key",
                        "invalid_fields": [
                            "segment_key"
                        ]
                    }
                }




## name: <ins>Get User Segments</ins>

desc: This API will give you the list of segments that the user is mapped to

method: **"GET"**

url: *"/v1/{partner-id}/user/{ext-user-id}/user_segments"*

example : /v1/12345bef00abc/user/123/user_segments

case:

success: **true**

              o/p: {
                  "success": true,
                  "response_code": 200,
                  "entity": "collection",
                  "count": 2,
                  "items": [
                      {
                          "id": 3404,
                          "segment_title": "Test One",
                          "key": "test_1"
                      },
                      {
                          "id": 2637,
                          "segment_title": "Test Two",
                          "key": "test_2"
                      },

                  ]
              }


success: **false**

            o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "INVALID_DATA",
                    "description": "Invalid Ext User Id",
                    "invalid_fields": [
                        "ext_user_id"
                    ]
                }
            }



## name: <ins>List all Quiz</ins>

desc: List all Quiz from collection return's array of quizzes

method: **"GET"**

url: *"/v1/{partner-id}/quizzes"*

query string: /quizzes?per_page=10&page=1

example : /v1/12345bef00abc/quizzes

case:

success: **true**

                 o/p: {
                        "success": true,
                        "response_code": 200,
                        "entity": "collection",
                        "count": 2,
                        "items": [
                            {
                                "id": 1773,
                                "name": "Test Quiz 01-J16",
                                "timer": 60,
                                "total_questions": 6,
                                "num_questions": 6,
                                "tenant_id": 11,
                                "created_at": "2024-01-16T07:25:03.527+05:30",
                                "updated_at": "2024-01-16T07:25:03.527+05:30"
                            },
                            {
                                "id": 1743,
                                "name": "Test Quiz-24",
                                "timer": 60,
                                "total_questions": 4,
                                "num_questions": 4,
                                "tenant_id": 11,
                                "created_at": "2024-01-02T15:57:49.064+05:30",
                                "updated_at": "2024-01-02T15:57:49.064+05:30"
                            },

                        ]
                }



## name: <ins>Set User Properties</ins>

desc: Set User Properties specified user

method: **"POST"**

url: *"/v1/{partner-id}/user/{ext-user-id}/properties"*

example : /v1/12345bef00abc/user/123/properties

          body: {
              "properties": {
                  "activation_date": "20 Jan 2020",
                  "age": 50
              }
          }

case:

success: **true**

              o/p: {
                  "success": true,
                  "response_code": 200,
                  "entity": "user",
                  "ext_user_id": "123",
                  "properties": {
                      "age": 50,
                      "test": 10,
                      "activation_date": "20 Jan 2020"
                  },
                  "created_at": 1599112736
              }

success: **false**

                o/p: {
                    "success": false,
                    "response_code": 422,
                    "error": {
                        "code": "INVALID_DATA",
                        "description": "Invalid Ext User Id.",
                        "invalid_fields": [
                            "ext_user_id"
                        ]
                    }
                }




## name: <ins>Get offers data</ins>

desc: Use this endpoint to retrieve the offers data for specific user

method: **"GET"**

url: *"/v1/{partner-id}/user/{ext-user-id}/offers"*

example : /v1/12345bef00abc/user/123/offers

case:

success: **true**

             o/p: {
                "success": true,
                "response_code": 200,
                "entity": "collection",
                "user_name": "000",
                "ext_uid": "000",
                "count": 3,
                "items": [
                    {
                        "title": "<p>aaa</p>",
                        "description": "<p>vvvdcddc</p>",
                        "show_banner": true,
                        "offer_type_code": "quiz",
                        "button_text": "Play",
                        "image_url": "1176"
                    },
                    {
                        "title": "Holi Campain3 ",
                        "description": "Holi Stamps with milestone",
                        "offer_type_code": "stamp_campaign",
                        "button_text": "Play"
                    },
                    {
                        "title": "<p>🎮🎮</p>",
                        "description": "<p>🎈Win Big🎉</p>",
                        "show_banner": true,
                        "offer_type_code": "game",
                        "button_text": "Play",
                        "image_url": "485"
                    }
                ]
            }

success: **false**

            o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "INVALID_DATA",
                    "description": "Invalid Ext User Id.",
                    "invalid_fields": [
                        "ext_user_id"
                    ]
                }
            }



## name: <ins>Sending Past Date User Event</ins>

desc: Sending Past Date User Event

method: **"POST"**

url: *"/v1/{partner-id}/user_previous_event"*

example : /v1/12345bef00abc/user_previous_event

         body: {
            "ext_user_id": "123", "event_key": "330", "event_data": {}, "firebase_token": "", "datetime": "12-05-2021 12:34:00"
         }

case:

success: **true**

              o/p: {
                  "success": true,
                  "response_code": 200,
                  "id": 1925575787,
                  "entity": "user_event",
                  "ext_user_id": "7828011085",
                  "event_key": "330",
                  "event_data": null,
                  "created_at": 1708085335,
                  "additional_data": {
                      "reward_generated": false,
                      "reward": null,
                      "campaign": null
                  }
              }

success: **false**

            o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "PARAMETERS_MISSING",
                    "description": "Missing event_key",
                    "missing_fields": [
                        "event_key"
                    ]
                }
            }





## name: <ins>Get Referral History</ins>

desc: Get Referral History

method: **"GET"**

url: *"/v1/{partner-id}/referral_history"*

example : /v1/12345bef00abc/referral_history

case:

success: **true**

              o/p:{
                "success": true,
                "response_code": 200,
                "entity": "referrals",
                "total_pages": 1,
                "current_page": 1,
                "total_count": 0,
                "referrals": []
            }




## name: <ins>Verify Referrer Code</ins>

desc: Verify Referrer Code

method: **"GET"**

url: *"/v1/{partner-id}/verify_referrer_code/{code}"*

example : /v1/12345bef00abc/verify_referrer_code/ABC

case:

success: **true**

             o/p: {
                "success": true,
                "response_code": 200,
                "entity": "referrer_code",
                "message": "Referrer Code Valid."
                "refer_code": "ABC"
            }

success: **false**

            o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "INVALID_DATA",
                    "description": "Invalid Referrer Code.",
                    "invalid_fields": [
                        "referrer_code"
                    ]
                }
            }




## name: <ins>Validate Referrer linked with a User</ins>

desc: Validate Referrer linked with a User

method: **"PUT"**

url: *"/v1/{partner-id}/user/{ext-user-id}/validate_referrer"*

example : /v1/12345bef00abc/user/123/validate_referrer

case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "message": "Successful"
            }


success: **false**

            o/p: {
              "success": false,
              "response_code": 422,
              "error": {
                  "code": "INVALID_DATA",
                  "description": "Invalid Ext User Id.",
                  "invalid_fields": [
                      "ext_user_id"
                  ]
              }
          }
          o/p: {
              "success": false,
              "response_code": 422,
              "message": "No Referrer linked with given User"
          }




## name: <ins>Validate User's Device Uniqueness</ins>

desc: Validate User's Device Uniqueness

method: **"GET"**

url: *"/v1/{partner-id}/user/{ext-user-id}/validate_device"*

example : /v1/12345bef00abc/user/123/validate_device

case:

success: **true**

             o/p: {
                "success": true,
                "response_code": 200,
                "is_uniq": false
            }


success: **false**

            o/p: {
                            "success": false,
                            "response_code": 422,
                            "error": {
                                "code": "INVALID_DATA",
                                "description": "Invalid Ext User Id.",
                                "invalid_fields": [
                                    "ext_user_id"
                                ]
                            }
                        }



## name: <ins>Update User's Referral Code</ins>

desc: Update User's Referral Code

method: **"PUT"**

url: *"/v1/{{partner-id}}/user/{{ext-user-id}}/update_referral_code/ABCD"*

example : /v1/12345bef00abc/user/123/update_referral_code/ABCD

case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "message": "Referral Code Updated"
            }

success: **false**

        o/p: {
            "success": false,
            "response_code": 422,
            "error": {
                "code": "INVALID_DATA",
                "description": "Invalid Ext User Id.",
                "invalid_fields": [
                    "ext_user_id"
                ]
            }
        }




## name: <ins>Delete users with GAID</ins>

desc: Delete users with GAID

method: **"POST"**

url: *"/v1/{{partner-id}}/users/reset_users"*

example : /v1/12345bef00abc/users/reset_users


        body:  {
            "gaid": "00000000-0000-0000-0000-000000000000"
        }


case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "user_action",
                "message": "Users deleted successfully"
            }

success: **false**

            o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "NO_DATA",
                    "description": "No User found with given GAID."
                }
            }



## name: <ins>Get Specific User's Referral History</ins>

desc: Get Specific User's Referral History

method: **"GET"**

url: *"/v1/{{partner-id}}/user/{{ext-user-id}}/referral_history?page=1"*

example : /v1/12345bef00abc/user/{{ext-user-id}}/referral_history

case:

success: **true**

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "referrals",
                "total_pages": 0,
                "current_page": 1,
                "total_count": 0,
                "referrals": []
            }

success: **false**

             o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "INVALID_DATA",
                    "description": "No Referrer Found."
                }
            }





## name: <ins>Get User IDs in a Segment</ins>

desc: Get User IDs in a Segment using Segment key

method: **"GET"**

url: *"/v1/{partner-id}/segments/{segment-key}"*

example : /v1/12345bef00abc/segments/test_segment

case:

success: **true**

            o/p:  "example": {
                  "success": true,
                  "response_code": 200,
                  "entity": "segment_users",
                  "segment_key": "newtest",
                  "segment_users": ["MNOP", "IJKL", "EFGH"]
                }

success: **false**

            o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "INVALID_DATA",
                    "description": "Invalid Segment Key",
                    "invalid_fields": [
                        "segment_key"
                    ]
                }
            }




## name: <ins>Quiz Tournaments</ins>

desc: Get Live Quiz Tournaments

method: **"GET"**

url: *"/v1/{{partner-id}}/quiz_tournaments"*

example : /v1/12345bef00abc/quiz_tournaments

case:

success: **true**

            o/p: "example": {
                  "success": true,
                  "message": "success",
                  "quiz_tournaments": [
                    {
                      "quiz_tournament_id": 2575,
                      "title": "Test week",
                      "offer_id": 17932,
                      "prize_type": "Cash",
                      "start_date": "06/02/2024",
                      "end_date": "20/02/2024",
                      "start_time": "15:53",
                      "end_time": "18:03",
                      "quiz_tournament_games": [
                        {
                          "id": 4580,
                          "starts_at": "2024-02-20T15:53:00.000+05:30",
                          "ends_at": "2024-02-20T18:03:00.000+05:30"
                        },
                        {
                          "id": 4579,
                          "starts_at": "2024-02-13T15:53:00.000+05:30",
                          "ends_at": "2024-02-13T18:03:00.000+05:30"
                        },
                        {
                          "id": 4578,
                          "starts_at": "2024-02-06T15:53:00.000+05:30",
                          "ends_at": "2024-02-06T18:03:00.000+05:30"
                        }
                      ]
                    }
                  ]
                },

success: **false**

            {
    "success": false,
    "message": "No Tournaments Live. Please Check back later"
}


## name: <ins>Unscartched Scratchcards</ins>

desc: List all Unscartched Scratchcards with specified from_date => to_date :or last 30days from today.

method: **"GET"**

url: *"/v1/{{partner-id}}/get_unscratched_scratchcards"*

example : /v1/12345bef00abc/get_unscratched_scratchcards?from_date=01-07-2023&to_date=30-07-2023

    query_parms:
                key: from_date    value: "01-01-2020"
                key: to_date    value: "10-01-2020"

case:

success: **true**

            o/p: {
                "success": true,
                "unscratched_scratchcards": [
                    {
                        "id": 49219744,
                        "offer_id": 12243,
                        "ref_num": "qwLJb",
                        "ext_uid": "124",
                        "value": 0,
                        "message": "Earned for dd",
                        "created_at": "2024-02-19T12:29:30.724+05:30"
                    },
                    {
                        "id": 49219745,
                        "offer_id": 12243,
                        "ref_num": "1Pgox",
                        "ext_uid": "1234_redected",
                        "value": 0,
                        "message": "Earned for dd",
                        "created_at": "2024-02-19T12:29:45.358+05:30"
                    },
                  ]
                },

success: **false**



        {
            "success": false,
            "message": "Unscartched Scartch Cards Not Present!"
        }


## name: <ins>Expiry Scratchcards</ins>

desc: Expire Scratch Card using ref_num of scratch_card, pass ref_num in array of request body to make it expired.

method: **"POST"**

url: *"/v1/{{partner-id}}/expiry_partner_scratchcards"*

example : /v1/12345bef00abc/expiry_partner_scratchcards

    body:{
            "is_expired": true,
            "expiration_message": "Uh oh!, You haven't redeemed your reward.",
            "ref_nums": ["UGUHx","xghLg"]
        }

case:

success: **true**

    o/p: {
        "success": true,
        "message": "Expiry Triggered"
    }




## name: <ins>Delete User</ins>

desc: Remove using from Flyy eco-syetem using user ext-uid

method: **"PUT"**

url: *"/v1/{{partner-id}}/delete_user/{{ext-uid}}"*

example : /v1/12345bef00abc/delete_user/1234


case:

success: **true**

        o/p: {
            "success": true,
            "message": "User Deleted Successfully.",
            "status": 200
        }

success: **false**

        {
            "success": false,
            "message": "User Not Found.",
            "status": 200
        }



## name: <ins>Transfer Requests,</ins>

desc: Transfer Requests api for accept or reject redemption.

method: **"PUT",**

url: *"/v1/{partner-id}/transfer_requests/{transfer_request_id}/{status}",*

example : /v1/12345bef00abc/transfer_requests/100/accept

case :

success: **true**


            o/p: {
                "success": true,
                "message": "Transfer Request with id 100 is under process. with status accept"
            },

example : /v1/12345bef00abc/transfer_requests/100/reject

            o/p: {
                "success": true,
                "message": "Transfer Request with id 100 is under process. with status reject"
            },

success: **false**

            1: status is "rejected"
                o/p: {
                        "success": false,
                        "message": "Redemption request Rejected"
                },

            2: status is in "process"
                o/p: {
                        "success": false,
                        "message": "Already Under Process"
                },
            3: account not exist
                o/p: {
                        "success": false,
                        "message": "Partner Bank Account Not Present"
                },
            4: Insufficient Balance:
                o/p: {
                        "success": false,
                        "message": "Low Balance"
                },
