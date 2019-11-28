.. _header-n0:

Exception code
===============

======== ===================================== =================================================
code      symbol                                description
======== ===================================== =================================================
100       FAIL                                  failed
200       SUCCESS                               returns successfully
400       APIError                              error request
403       FORBIDDEN                             no permission
404       RESOURCE_NOT_FOUND                    resource does not exist
500       INTERNAL_ERROR                        server processing failed
600       PARAMETER_INVALID                     illegal parameter
601       PARAMETER_CANT_BE_EMPTY               missing required parameters
602       NEED_USER_LOGIN                       requires user login
603       ILLEGAL_PROTOCOL                      illegal request
604       VALIDATE_CODE_ERROR                   mobile verification code error
605       VINSUFFICIENT_PERMISSIONS             insufficient permissions
606       VALIDATE_COMMOM_CODE_ERROR            verification code error
607       VALIDATE_SEND_CODE_ERROR              verification code failed to send
700       DO_NOT_HAVE_ANY_MORE_RECORD           no more records
800       ACCOUNT_BINDING_USER_NULL             account does not exist
801       ACCOUNT_NOT_BINDING                   device not bound
802       ACCOUNT_BINDING_FAIL                  device binding failed
804       ACCOUNT_LOCKED                        account disabled
805       ACCOUNT_USERNAME_PASSWORD_FAIL        username/password invalid
806       ACCOUNT_UNIONID_FAIL                  account is not bound to a third-party user
807       ACCOUNT_PHONE_FAIL                    phone number is not bound to a third-party user
808       ACCOUNT_UNIONID_PHONE                 phone number is already bound to other user
809       ACCOUNT_WEIXIN_FAIL                   Wechat login failed
810       ACCOUNT_WEIBO_FAIL                    Weibo login failed
811       ACCOUNT_LOGOUT_FAIL                   logout failed
812       ACCOUNT_LOGIN_IPLIMITFAIL IP          address is prohibited
813       ACCOUNT_QQ_FAIL QQ                    login failed
814       NOREPEAT_SELECT_SOFTWARE              unable to select common software repeatedly
815       ACCOUNT_UNIONID_EXISTS UNIONID        already exists
900       VALIDATE_PHONE_FAIL                   phone number already exists
901       VALIDATE_EMAIL_FAIL                   mailbox already exists
902       VALIDATE_USERNAME_FAIL                username already exists
903       ACCOUNT_EMAIL_FAIL                    mailbox is not bound to an account
904       CURRENCY_NOT_SUPPORT                  unsupported currency
905       AGENT_NOT_SUPPORT                     unsupport agent
906       AMOUNT_NOT_SUPPORT                    please enter a reasonable recharge value
908       COUPONNO_NOT_SUPPORT                  coupon code is not supported
909       PAYMETHOD_NOT_SUPPORT                 unsupported payment method
910       NO_INVOICE_ORDER                      invoice order unavailable
911       NO_INVOICE_ADDRESS                    invoice order address unavailable
912       SUBUSER_EXISTS_TASKS                  unable to delete a sub-user with executing tasks
913       SUBUSER_ARREARAGE                     sub-user is overdue
914       DELSUBUSER_EXISTS_BALANCE             there is balance for the sub-user to be deleting
915       NO_INVOICE_TEMPLATE                   invoice information unavailable
916       RECEIPT_TYPE_ERROR                    invoice type not match
920       NO_LATEST_VERSION                     no latest client version
1000      REDIS_CACHE_FAIL                      redis cache exception
1000000   RayvisionError                        python exception
======== ===================================== =================================================
