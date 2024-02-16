Api:
name: Transfer Requests,
desc: Transfer Requests api for accept or reject redemption.,
method: "PUT",
url: "/v1/{partner-id}/transfer_requests/{transfer_request_id}/{status}",
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
            fail cases:
            
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
