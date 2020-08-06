---
title: リモートサーバー上の負荷分散パッケージのログ記録Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b45fa6607d6edc1559d8ebcbbbc7598e11eac408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641069"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a><span data-ttu-id="70478-102">リモート サーバー上の負荷分散パッケージのログ記録</span><span class="sxs-lookup"><span data-stu-id="70478-102">Logging for Load Balanced Packages on Remote Servers</span></span>
  <span data-ttu-id="70478-103">すべての子パッケージで同じログ プロバイダーを使用し、これらの出力先を同じにすれば、さまざまなサーバーで実行されているすべての子パッケージに関するログの管理が容易になります。</span><span class="sxs-lookup"><span data-stu-id="70478-103">It is easier for an administrator to manage the logs for all the child packages that are running on various servers when all the child packages use the same log provider and they all write to the same destination.</span></span> <span data-ttu-id="70478-104">すべての子パッケージに共通するログ ファイルを作成する方法の 1 つとして、イベントのログが SQL Server ログ プロバイダーに記録されるように子パッケージを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="70478-104">One way that you can create a common log file for all child packages is to configure the child packages to log their events to a SQL Server log provider.</span></span> <span data-ttu-id="70478-105">すべてのパッケージが、同じデータベース、同じサーバー、同じサーバー インスタンスを使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="70478-105">You can configure all the packages to use the same database, the same server, and the same instance of the server.</span></span>  
  
 <span data-ttu-id="70478-106">管理者は、1 台のサーバーにログオンするだけで、すべての子パッケージに関するログ ファイルを確認できます。</span><span class="sxs-lookup"><span data-stu-id="70478-106">To view the log files, the administrator only has to log on to a single server to view the log files for all child packages.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="70478-107">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="70478-107">Related Tasks</span></span>  
 <span data-ttu-id="70478-108">パッケージでログ記録を有効にする方法については、「 [SQL Server Data Tools でパッケージのログ記録を有効にする](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70478-108">For information about how to enable logging in a package, see [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70478-109">参照</span><span class="sxs-lookup"><span data-stu-id="70478-109">See Also</span></span>  
 [<span data-ttu-id="70478-110">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="70478-110">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
