---
title: SQL Server エラー ログの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8acc27150f42049384e2789ef83ae66a737da9bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645853"
---
# <a name="configure-sql-server-error-logs"></a><span data-ttu-id="987bc-102">SQL Server エラー ログの構成</span><span class="sxs-lookup"><span data-stu-id="987bc-102">Configure SQL Server Error Logs</span></span>
  <span data-ttu-id="987bc-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを再利用する方法を表示したり、変更したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="987bc-103">This topic describes how to view or modify the way [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error logs are recycled.</span></span>  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a><span data-ttu-id="987bc-104">[SQL Server エラー ログの構成] ダイアログ ボックスを開くには</span><span class="sxs-lookup"><span data-stu-id="987bc-104">To open the Configure SQL Server Error Logs dialog box</span></span>  
  
1.  <span data-ttu-id="987bc-105">オブジェクト エクスプローラーで、使用している SQL Server のインスタンスを展開し、 **[管理]** を展開します。次に、 **[SQL Server ログ]** を右クリックし、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="987bc-105">In Object Explorer, expand the instance of SQL Server, expand **Management**, right-click **SQL Server Logs**, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="987bc-106">**[SQL Server エラー ログの構成]** ダイアログ ボックスで、次のオプションから選択します。</span><span class="sxs-lookup"><span data-stu-id="987bc-106">In the **Configure SQL Server Error Logs** dialog box, choose from the following options.</span></span>  
  
     <span data-ttu-id="987bc-107">**[再利用する前に、エラー ログ ファイルの数を制限する]**</span><span class="sxs-lookup"><span data-stu-id="987bc-107">**Limit the number of the error log files before they are recycled**</span></span>  
     <span data-ttu-id="987bc-108">再利用されるまでに作成されるエラー ログの数を制限する場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="987bc-108">Check to limit the number of error logs created before they are recycled.</span></span> <span data-ttu-id="987bc-109">新しいエラー ログは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを起動するたびに作成されます。</span><span class="sxs-lookup"><span data-stu-id="987bc-109">A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="987bc-110">では、このチェック ボックスをオンにし、エラー ログ ファイルの最大数に別の数を指定しない限り、6 つ前までのログのバックアップが保持されます。</span><span class="sxs-lookup"><span data-stu-id="987bc-110">retains backups of the previous six logs, unless you check this option, and specify a different maximum number of error log files below.</span></span>  
  
     <span data-ttu-id="987bc-111">**[エラー ログ ファイルの最大数]**</span><span class="sxs-lookup"><span data-stu-id="987bc-111">**Maximum number of error log files**</span></span>  
     <span data-ttu-id="987bc-112">再利用されるまでに作成されるエラー ログ ファイルの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="987bc-112">Specify the maximum number of error log files created before they are recycled.</span></span> <span data-ttu-id="987bc-113">既定値は 6 で、これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再利用するまで保有している以前のバックアップ ログの数と同じです。</span><span class="sxs-lookup"><span data-stu-id="987bc-113">The default is 6, which is the number of previous backup logs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retains before recycling them.</span></span>  
  
  
