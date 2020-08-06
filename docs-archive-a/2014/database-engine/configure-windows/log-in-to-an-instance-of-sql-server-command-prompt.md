---
title: SQL Server インスタンスへのログイン (コマンド プロンプト) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 32028a30786117f2cafa76150867a0e726b07cda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632096"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a><span data-ttu-id="b1958-102">SQL Server インスタンスへのログイン (コマンド プロンプト)</span><span class="sxs-lookup"><span data-stu-id="b1958-102">Log In to an Instance of SQL Server (Command Prompt)</span></span>
  <span data-ttu-id="b1958-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sqlcmd **ユーティリティを使用して** のインスタンスへの接続をテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1958-103">This topic describes how to test connectivity to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the **sqlcmd** utility.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a><span data-ttu-id="b1958-104">SQL Server の既定のインスタンスにログインするには</span><span class="sxs-lookup"><span data-stu-id="b1958-104">To log in to the default instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="b1958-105">コマンド プロンプトで次のコマンドを入力し、Windows 認証を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="b1958-105">From a command prompt, enter the following command to connect by using Windows Authentication:</span></span>  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a><span data-ttu-id="b1958-106">SQL Server の名前付きインスタンスにログインするには</span><span class="sxs-lookup"><span data-stu-id="b1958-106">To log in to a named instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="b1958-107">コマンド プロンプトで次のコマンドを入力し、Windows 認証を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="b1958-107">From a command prompt, enter the following command to connect by using Windows Authentication:</span></span>  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b1958-108">参照</span><span class="sxs-lookup"><span data-stu-id="b1958-108">See Also</span></span>  
 <span data-ttu-id="b1958-109">[sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b1958-109">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="b1958-110">osql ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="b1958-110">osql Utility</span></span>](../../tools/osql-utility.md)  
  
  
