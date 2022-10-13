#inncom #dian #dian-3180 

[$look up 關聯用語法](https://www.stackchief.com/tutorials/%24lookup%20Examples%20%7C%20MongoDB)

# db collections
## members
-   mobile
-   payments (one to few)
	-   orderNo 
	-   amount
	-   appointments (one to many + 反正規化)
		-   id
	        -   date → 修改預約資訊的時候要記得改這邊
	-   auth
		- status → 付款後會改 [[DIAN-3180 刷卡完成]]
	-   ...
-   allowPayments

## appointments
> 新增到行事曆則新增一筆。 [[DIAN-3180 新增行事曆]]
> 一個時段最多三筆。
> 因為可能沒有對應的 member，所以一定要獨立出來。
-   date
-   *time*
-   *colorLabel* → 顏色
-   *type* → 套餐
-   *contact*(object)
	-   mobile → 開放刷卡時用來關聯 [[DIAN-3180 開放刷卡]]
	-   name → 卡位用，僅供行事曆顯示
-   *note*
-   *paymentStatus* → null, cash, creditCardWaiting, creditCardDone 依照不同狀態去操作
-   name
-   twid 
-   birthdate
-   mobile
-   address
-   receiverName
-   receiverMobile