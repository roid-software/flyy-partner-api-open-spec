Api: Flyy Partner

//

name: Get offers data

desc: Use this endpoint to retrieve the offers data for specific user

method: "GET"

url: "/v1/{partner-id}/quizzes"

query string: /quizzes?per_page=10&page=1

example : /v1/12345bef00abc/quizzes

case:

success: true

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

//

name: Set User Properties

desc: Set User Properties specified user

method: "POST"

url: "/v1/{partner-id}/user/{ext-user-id}/properties"

example : /v1/12345bef00abc/user/123/properties

          body: {
              "properties": {
                  "activation_date": "20 Jan 2020",
                  "age": 50
              }
          }

case:

success: true

              o/p: {
                  "success": true,
                  "response_code": 200,
                  "entity": "user",
                  "ext_user_id": "7828011085",
                  "properties": {
                      "age": 50,
                      "test": 10,
                      "activation_date": "20 Jan 2020"
                  },
                  "created_at": 1599112736
              }

success: false

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


//

name: Get offers data

desc: Use this endpoint to retrieve the offers data for specific user

method: "GET"

url:"/v1/{partner-id}/user/{ext-user-id}/offers"

example : /v1/12345bef00abc/user/123/offers

case:

success: true

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

success: false

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

//

name: Sending Past Date User Event

desc: Sending Past Date User Event

method: "POST"

url:"/v1/{partner-id}/user_previous_event"

example : /v1/12345bef00abc/user_previous_event

         body: { 
            "ext_user_id": "7828011085", "event_key": "330", "event_data": {}, "firebase_token": "", "datetime": "12-05-2021 12:34:00"
         }

case:

success: true

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

success: false

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
 


//

name: Get Referral History

desc: Get Referral History

method: "GET"

url: "/v1/{partner-id}/referral_history"

example : /v1/12345bef00abc/referral_history

case:

success: true

              o/p:{
                "success": true,
                "response_code": 200,
                "entity": "referrals",
                "total_pages": 1,
                "current_page": 1,
                "total_count": 0,
                "referrals": []
            }


//

name: Verify Referrer Code

desc: Verify Referrer Code

method: "GET"

url: "/v1/{partner-id}/verify_referrer_code/{code}"

example : /v1/12345bef00abc/verify_referrer_code/ABC

case:

success: true

             o/p: {
                "success": true,
                "response_code": 200,
                "entity": "referrer_code",
                "message": "Referrer Code Valid."
                "refer_code": "ABC"
            }

success: false

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


//

name: Validate Referrer linked with a User

desc: Validate Referrer linked with a User

method: "GET"

url: "/v1/{partner-id}/user/{ext-user-id}/validate_referrer"

example : /v1/12345bef00abc/user/123/validate_referrer

case:

success: true

            o/p: {
                "success": true,
                "response_code": 200,
                "message": "Successful"
            }


success: false

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


//

name: Validate User's Device Uniqueness

desc: Validate User's Device Uniqueness

method: "GET"

url: "/v1/{partner-id}/user/{ext-user-id}/validate_device"

example : /v1/12345bef00abc/user/123/validate_device

case:

success: true

             o/p: {
                "success": true,
                "response_code": 200,
                "is_uniq": false
            }


success: false

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

//

name: Update User's Referral Code

desc: Update User's Referral Code

method: "PUT"

url: "/v1/{{partner-id}}/user/{{ext-user-id}}/update_referral_code/ABCD"

example : /v1/12345bef00abc/user/123/update_referral_code/ABCD

case:

success: true

            o/p: {
                "success": true,
                "response_code": 200,
                "message": "Referral Code Updated"
            }

success: false

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


//

name: Delete users with GAID

desc: Delete users with GAID

method: "POST"

url: "/v1/{{partner-id}}/users/reset_users"

example : /v1/12345bef00abc/users/reset_users


        body:  {
            "gaid": "00000000-0000-0000-0000-000000000000"    
        }


case:

success: true

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "user_action",
                "message": "Users deleted successfully"
            }

success: false

            o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "NO_DATA",
                    "description": "No User found with given GAID."
                }
            }

//

name: Get Specific User's Referral History

desc: Get Specific User's Referral History

method: "GET"

url: "/v1/{{partner-id}}/user/{{ext-user-id}}/referral_history?page=1"

example : /v1/12345bef00abc/user/{{ext-user-id}}/referral_history

case:

success: true

            o/p: {
                "success": true,
                "response_code": 200,
                "entity": "referrals",
                "total_pages": 0,
                "current_page": 1,
                "total_count": 0,
                "referrals": []
            }

success: false

             o/p: {
                "success": false,
                "response_code": 422,
                "error": {
                    "code": "INVALID_DATA",
                    "description": "No Referrer Found."
                }
            }



//

name: Get User IDs in a Segment

desc: Get User IDs in a Segment using Segment key

method: "GET"

url: "/v1/{partner-id}/segments/{segment-key}"

example : /v1/12345bef00abc/segments/test_segment

case:

success: true

            o/p:  "example": {
                  "success": true,
                  "response_code": 200,
                  "entity": "segment_users",
                  "segment_key": "newtest",
                  "segment_users": ["MNOP", "IJKL", "EFGH"]
                }

success: false

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


//

name: Quiz Tournaments

desc: Get Live Quiz Tournaments

method: "GET"

url: "/v1/{{partner-id}}/quiz_tournaments"

example : /v1/12345bef00abc/quiz_tournaments

case:

success: true

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
                
success: false

            {
    "success": false,
    "message": "No Tournaments Live. Please Check back later"
}


//

name: Transfer Requests,

desc: Transfer Requests api for accept or reject redemption.

method: "PUT",

url: "/v1/{partner-id}/transfer_requests/{transfer_request_id}/{status}",

case :

success: true

example : /v1/12345bef00abc/transfer_requests/100/accept

            o/p: {
                "success": true,
                "message": "Transfer Request with id 100 is under process. with status accept"
            },
            
example : /v1/12345bef00abc/transfer_requests/100/reject

            o/p: {
                "success": true,
                "message": "Transfer Request with id 100 is under process. with status reject"
            },
            
success: false

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
