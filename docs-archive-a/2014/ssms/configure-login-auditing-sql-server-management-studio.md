---
title: ログインの監査の構成 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7e05f6c254e098a67a5ce00435c009cd450af44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645312"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a><span data-ttu-id="ce70c-102">ログインの監査の構成 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ce70c-102">Configure Login Auditing (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ce70c-103">このトピックでは、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のログイン操作を監視するために [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] でログインの監査を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ce70c-103">This topic describes how to configure login auditing in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] to monitor [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] login activity.</span></span> <span data-ttu-id="ce70c-104">次のイベントが発生したときにエラー ログに書き込むように、ログインの監査を構成できます。</span><span class="sxs-lookup"><span data-stu-id="ce70c-104">Login auditing can be configured to write to the error log on the following events.</span></span>  
  
-   <span data-ttu-id="ce70c-105">ログインの失敗</span><span class="sxs-lookup"><span data-stu-id="ce70c-105">Failed logins</span></span>  
  
-   <span data-ttu-id="ce70c-106">ログインの成功</span><span class="sxs-lookup"><span data-stu-id="ce70c-106">Successful logins</span></span>  
  
-   <span data-ttu-id="ce70c-107">[失敗したログインと成功したログインの両方]</span><span class="sxs-lookup"><span data-stu-id="ce70c-107">Both failed and successful logins</span></span>  
  
 <span data-ttu-id="ce70c-108">このオプションを有効にするには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce70c-108">You must restart [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] before this option will take effect.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ce70c-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ce70c-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-login-auditing"></a><span data-ttu-id="ce70c-110">ログインの監査を構成するには</span><span class="sxs-lookup"><span data-stu-id="ce70c-110">To configure login auditing</span></span>  
  
1.  <span data-ttu-id="ce70c-111">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、オブジェクト エクスプローラーを使用して [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ce70c-111">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] with Object Explorer.</span></span>  
  
2.  <span data-ttu-id="ce70c-112">オブジェクト エクスプローラーでサーバー名を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ce70c-112">In Object Explorer, right-click the server name, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="ce70c-113">**[セキュリティ]** ページの **[ログインの監査]** で、必要なオプションをクリックし、 **[サーバーのプロパティ]** ページを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ce70c-113">On the **Security** page, under **Login** auditing, click the desired option and close the **Server Properties** page.</span></span>  
  
4.  <span data-ttu-id="ce70c-114">オブジェクト エクスプローラーでサーバー名を右クリックし、 **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ce70c-114">In Object Explorer, right-click the server name, and then click **Restart**.</span></span>  
  
  
