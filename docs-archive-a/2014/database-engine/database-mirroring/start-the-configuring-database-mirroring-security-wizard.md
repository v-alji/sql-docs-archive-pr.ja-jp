---
title: データベースミラーリングセキュリティ構成ウィザードを開始する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], security
- Configuring Database Mirroring Security Wizard
ms.assetid: 1c846950-0a2d-45df-b0d5-193e455f7cd5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fab3a0a48633f70a91d4e65bd31b7d3f9c314ca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644633"
---
# <a name="start-the-configuring-database-mirroring-security-wizard-sql-server-management-studio"></a><span data-ttu-id="8171c-102">データベース ミラーリング セキュリティ構成ウィザードの起動 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8171c-102">Start the Configuring Database Mirroring Security Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8171c-103">データベース ミラーリング セキュリティ構成ウィザードを使用して、ミラーリングで使用されるすべてまたは一部のサーバー インスタンスでセキュリティ設定を初期構成できます。</span><span class="sxs-lookup"><span data-stu-id="8171c-103">The Configure Database Mirroring Security Wizard can be used to initially configure security settings at all or some server instances involved in mirroring.</span></span> <span data-ttu-id="8171c-104">このウィザードは、 **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページから開きます。</span><span class="sxs-lookup"><span data-stu-id="8171c-104">This wizard works in conjunction with the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
### <a name="to-launch-the-configure-database-mirroring-security-wizard"></a><span data-ttu-id="8171c-105">データベース ミラーリング セキュリティ構成ウィザードを起動するには</span><span class="sxs-lookup"><span data-stu-id="8171c-105">To launch the Configure Database Mirroring Security Wizard</span></span>  
  
1.  <span data-ttu-id="8171c-106">プリンシパル サーバー インスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックして、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="8171c-106">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="8171c-107">**[データベース]** を展開し、ミラー化するデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="8171c-107">Expand **Databases**, and select the database to be mirrored.</span></span>  
  
3.  <span data-ttu-id="8171c-108">データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8171c-108">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="8171c-109">[**データベースのプロパティ**] ダイアログボックスの [[ミラーリング] ページ](../../relational-databases/databases/database-properties-mirroring-page.md)が開きます。</span><span class="sxs-lookup"><span data-stu-id="8171c-109">This opens the [Mirroring Page](../../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="8171c-110">**[セキュリティの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8171c-110">Click **Configure Security**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8171c-111">参照</span><span class="sxs-lookup"><span data-stu-id="8171c-111">See Also</span></span>  
 <span data-ttu-id="8171c-112">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8171c-112">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="8171c-113">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="8171c-113">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 [<span data-ttu-id="8171c-114">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8171c-114">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
  
