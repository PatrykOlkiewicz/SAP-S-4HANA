1. Based on config we woudl like to creata already order with late confirmation from vendor. So we need to change document date to have min 3 days old.  create order with previous conigured confirmation key.(C:\Users\patry\Documents\GitHub\SAP-S-4HANA\MM\confirmations\confirmations-settings). 
(screen1)
2. to enable any reminders in me92f we need to ganarate massage to vendor with ask for confirmation. To ganarate this massaage we need marked checkbox acknowl.reqd. to correctly set this go to ("C:\Users\Patryk.OLKIEWICZ\OneDrive - Groupe Limagrain Holding\Pulpit\PATRYK\MM\confirmations\NEU")
(SCREEN2)
PDF after saving should be generated:
(screen3)
ME92F transaction would be work if: NEU OUTPUT have been completed
(screen4)

3. ( in me92f you can send reminders if delivery is late) in our case confirmation is late so we use me92f. To not create manualy output parameters we cen create automatic expected output in mn04/mn05 (C:\Users\Patryk.OLKIEWICZ\OneDrive - Groupe Limagrain Holding\Pulpit\PATRYK\MM\confirmations\auto-output-config)

4.PUT parameter for which document should be generated 
5. mark orders for which output should be genereted and clck genereta massages
(screen5)

After saving output in pdf should be genereted automaticaly
(screen6)

6. After we have got confirmation from the vendor we come back to order and fill with AB confirmation.
(screen7)
In MD04 we can see the status in MRPelement have been changed to ShipNot it is connected wit our customizng of AB MRP relevant if this customizing wouldnt be heare status became the same and nothing will hapend.
(SCREEN8)

7. Instead of typing the next step manually, we will let the system generate it, just like a real warehouse integration. Go to VL31N. Stock playcement and fill the "PutawayQty"
(screen9)

9. Based on confirmation control key customizing in hedader if autoReg/GR is :
- 0 not relevant then - status stay the same but inbound delivery number is added in the row
- 1 reg automatically - in md04 status is changed after vl31n to Put Away
- 2 register and recive automatically - based on vl31n auto 101 movent is posted and order is not visible in md04
- 3


