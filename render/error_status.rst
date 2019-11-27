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
404       RESOURCE\ *NOT*\                      resource does not exist
500       INTERNAL_ERROR                        server processing failed
600       PARAMETER_INVALID                     illegal parameter
601       PARAMETER\ *CANT*\ BE_EMPTY           missing required parameters
602       NEED\ *USER*\ LOGIN                   requires user login
603       ILLEGAL_PROTOCOL                      illegal request
604       VALIDATE\ *CODE*\ ERROR               mobile verification code error
605       VINSUFFICIENT_PERMISSIONS             insufficient permissions
606       VALIDATE\ *COMMOM*\ CODE_ERROR        verification code error
607       VALIDATE\ *SEND*\ CODE_ERROR          verification code failed to send
700       DO\ *NOT*\ HAVE\ *ANY*\ MORE_RECORD   no more records
800       ACCOUNT\ *BINDING*\ USER_NULL         account does not exist
801       ACCOUNT\ *NOT*\ BINDING               device not bound
802       ACCOUNT\ *BINDING*\ FAIL              device binding failed
804       ACCOUNT_LOCKED                        account disabled
805       ACCOUNT\ *USERNAME*\ PASSWORD_FAIL    username/password invalid
806       ACCOUNT\ *UNIONID*\ FAIL              account is not bound to a third-party user
807       ACCOUNT\ *PHONE*\ FAIL                phone number is not bound to a third-party user
808       ACCOUNT\ *UNIONID*\ PHONE             phone number is already bound to other user
809       ACCOUNT\ *WEIXIN*\ FAIL               Wechat login failed
810       ACCOUNT\ *WEIBO*\ FAIL                Weibo login failed
811       ACCOUNT\ *LOGOUT*\ FAIL               logout failed
812       ACCOUNT\ *LOGIN*\ IPLIMITFAIL IP      address is prohibited
813       ACCOUNT\ *QQ*\ FAIL QQ                login failed
814       NOREPEAT\ *SELECT*\ SOFTWARE          unable to select common software repeatedly
815       ACCOUNT\ *UNIONID*\ EXISTS UNIONID    already exists
900       VALIDATE\ *PHONE*\ FAIL               phone number already exists
901       VALIDATE\ *EMAIL*\ FAIL               mailbox already exists
902       VALIDATE\ *USERNAME*\ FAIL            username already exists
903       ACCOUNT\ *EMAIL*\ FAIL                mailbox is not bound to an account
904       CURRENCY\ *NOT*\ SUPPORT              unsupported currency
905       AGENT\ *NOT*\ SUPPORT                 unsupport agent
906       AMOUNT\ *NOT*\ SUPPORT                please enter a reasonable recharge value
908       COUPONNO\ *NOT*\ SUPPORT              coupon code is not supported
909       PAYMETHOD\ *NOT*\ SUPPORT             unsupported payment method
910       NO\ *INVOICE*\ ORDER                  invoice order unavailable
911       NO\ *INVOICE*\ ADDRESS                invoice order address unavailable
912       SUBUSER\ *EXISTS*\ TASKS              unable to delete a sub-user with executing tasks
913       SUBUSER_ARREARAGE                     sub-user is overdue
914       DELSUBUSER\ *EXISTS*\ BALANCE         there is balance for the sub-user to be deleting
915       NO\ *INVOICE*\ TEMPLATE               invoice information unavailable
916       RECEIPT\ *TYPE*\ ERROR                invoice type not match
920       NO\ *LATEST*\ VERSION                 no latest client version
1000      REDIS\ *CACHE*\ FAIL                  redis cache exception
1000000   RayvisionError                        python exception
======== ===================================== =================================================
