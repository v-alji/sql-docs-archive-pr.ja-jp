---
title: Database Mail XPs サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33ee15e862e0992f39373ec30275040c4fcacc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642282"
---
# <a name="database-mail-xps-server-configuration-option"></a><span data-ttu-id="cf554-102">Database Mail XPs サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="cf554-102">Database Mail XPs Server Configuration Option</span></span>
  <span data-ttu-id="cf554-103">**Database Mail XPs** オプションを使用して、サーバーのデータベース メールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="cf554-103">Use the **DatabaseMail XPs** option to enable Database Mail on this server.</span></span> <span data-ttu-id="cf554-104">指定できる値は、</span><span class="sxs-lookup"><span data-stu-id="cf554-104">The possible values are:</span></span>  
  
-   <span data-ttu-id="cf554-105">**0** : データベース メールが使用できないことを示します (既定値)。</span><span class="sxs-lookup"><span data-stu-id="cf554-105">**0** indicating Database Mail is not available (default).</span></span>  
  
-   <span data-ttu-id="cf554-106">**1** : データベース メールが使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="cf554-106">**1** indicating Database Mail is available.</span></span>  
  
 <span data-ttu-id="cf554-107">この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="cf554-107">The setting takes effect immediately without a server stop and restart.</span></span>  
  
 <span data-ttu-id="cf554-108">データベース メールを使用するには、データベース メールを有効にしてから、データベース メールのホスト データベースを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf554-108">After enabling Database Mail, you must configure a Database Mail host database to use Database Mail.</span></span>  
  
 <span data-ttu-id="cf554-109">**データベース メール構成ウィザード** を使用してデータベース メールを構成すると、 **msdb** データベースのデータベース メール拡張ストアド プロシージャが有効になります。</span><span class="sxs-lookup"><span data-stu-id="cf554-109">Configuring Database Mail using the **Database Mail Configuration Wizard** enables the Database Mail extended stored procedures in the **msdb** database.</span></span> <span data-ttu-id="cf554-110">**データベース メール構成ウィザード**を使用する場合、以下の例の **sp_configure** を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cf554-110">If you use the **Database Mail Configuration Wizard**, you do not have to use the **sp_configure** example below.</span></span>  
  
 <span data-ttu-id="cf554-111">**Database Mail XPs** オプションを 0 に設定すると、データベース メールは開始されません。</span><span class="sxs-lookup"><span data-stu-id="cf554-111">Setting the **Database Mail XPs** option to 0 prevents Database Mail from starting.</span></span> <span data-ttu-id="cf554-112">データベース メールが実行されている場合にこのオプションを 0 に設定すると、 **DatabaseMailExeMinimumLifeTime** オプションで設定したアイドル状態の時間が続くまで、データベース メールは継続して実行され、メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="cf554-112">If it is running when the option is set to 0, it continues to run and send mail until it is idle for the time configured in the **DatabaseMailExeMinimumLifeTime** option.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cf554-113">例</span><span class="sxs-lookup"><span data-stu-id="cf554-113">Examples</span></span>  
 <span data-ttu-id="cf554-114">次の例では、データベース メール拡張ストアド プロシージャが有効になります。</span><span class="sxs-lookup"><span data-stu-id="cf554-114">The following example enables the Database Mail extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf554-115">参照</span><span class="sxs-lookup"><span data-stu-id="cf554-115">See Also</span></span>  
 [<span data-ttu-id="cf554-116">データベース メール</span><span class="sxs-lookup"><span data-stu-id="cf554-116">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
