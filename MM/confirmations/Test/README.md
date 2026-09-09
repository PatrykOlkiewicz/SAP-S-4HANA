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
