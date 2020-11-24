# WMI

> Doran Kayoumi, Jérôme Arn

1. Retrouvez les caractéristiques de votre processeur, en utilisant les différents outils installés 

> WMI explorer

| SELECT * FROM Win32_Processor WHERE DeviceID='CPU0' | SELECT * FROM Win32_Processor WHERE DeviceID='CPU1' |
| --------------------------------------------------- | --------------------------------------------------- |
| \\DESKTOP-T3Q31C8\ROOT\CIMV2:Win32_Processor        | \DESKTOP-T3Q31C8\ROOT\CIMV2:Win32_Processor         |
| ![](img/1_cpu0.png)                                 | ![](img/1_cpu1.png)                                 |

> WMI Monitor

Une fois la première configuration effectuée, on clique sur le bouton **Browse WMI Counters** et on sélectionne **Win32_Processor** puis les informations que l'on désire obtenir sur le processeur. 

![](img/1_wmim.png)

2. Retrouvez le SID de l’utilisateur Administrateur de votre système, en utilisant les différents outils installés

> WMI Monitor

Même chose qu'à la manipulation précédente mais cette fois sur la classe UserAccount.

![](img/2_wmim.png)

Et on peut constater le résultat dans l'active directory.

![](img/2_wmim2.png)

> WMI explorer

| SELECT * FROM Win32_UserAccount WHERE Domain='DESKTOP-T3Q31C8' AND Name='Administrateur' |
| ------------------------------------------------------------ |
| \\DESKTOP-T3Q31C8\ROOT\CIMV2:Win32_UserAccount.Domain        |
| ![](img/2_admin.png)                                         |





3. Retrouvez les routes IPv4 de votre système, en utilisant les différents outils installés

> WMI Monitor

Dans cette manipulation on peut sélectionner pour chaque route quel attribut on veut afficher. 

![](img/3_wmim.png)


> WMI explorer

| SELECT * FROM Win32_IP4RouteTable                            |
| ------------------------------------------------------------ |
| \\DESKTOP-T3Q31C8\ROOT\CIMV2:Win32_IP4RouteTable.Destination |
| ![](img/3_ip4.png)                                           |


> wmic

````shell
path win32_IP4RouteTable
````

![](img/3_wmic.png)


> wbemtest

![](img/3_wbemtest.png)


> PowerShell

````powershell
Get-WmiObject -query "SELECT * FROM Win32_IP4RouteTable" 
````

4. Toujours depuis la VM Windows A, à l’aide de WMI Monitor, affichez la quantité de mémoire disponible sur la machine Windows B.

> Montrez le trafic entre la VM Windows A et la VM Windows B à l’aide d’une capture Wireshark.

5. Toujours depuis la VM Windows A, écrivez un script PowerShell qui permette de lister les partitions de la machine Windows B avec leur lettre de lecteur et de retourner le pourcentage d’espace vide.

> En cas d’espace insuffisant, une alarme syslog est générée.