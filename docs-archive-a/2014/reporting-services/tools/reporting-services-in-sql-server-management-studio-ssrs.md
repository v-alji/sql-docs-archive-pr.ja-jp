---
title: SQL Server Management Studio の Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], how-to topics
ms.assetid: 60685458-9108-47bf-820a-5e7db454d408
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f4083d8b288c8816925723f4cfaef4342dd0298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721044"
---
# <a name="reporting-services-in-sql-server-management-studio-ssrs"></a><span data-ttu-id="5227f-102">SQL Server Management Studio の Reporting Services (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5227f-102">Reporting Services in SQL Server Management Studio (SSRS)</span></span>
  <span data-ttu-id="5227f-103">レポート サーバー管理者は [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="5227f-103">Report server administrators can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to:</span></span>  
  
-   <span data-ttu-id="5227f-104">機能を有効化し、サーバーの既定値を設定して、実行中のジョブを管理する。</span><span class="sxs-lookup"><span data-stu-id="5227f-104">Enable features, set server defaults, and manage running jobs.</span></span>  
  
-   <span data-ttu-id="5227f-105">カスタム レポートを表示および作成する。</span><span class="sxs-lookup"><span data-stu-id="5227f-105">View and create custom reports.</span></span> <span data-ttu-id="5227f-106">オブジェクト エクスプローラーでは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]と共にインストールされた一連の標準レポートが多数のノードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5227f-106">In Object Explorer, many nodes display a set of standard reports that are installed with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="5227f-107">管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="5227f-107">You must have administrator permissions.</span></span> <span data-ttu-id="5227f-108">カスタム レポートのスキーマは、インストールされているレポートのスキーマと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5227f-108">The schema of a custom report must match the schema of the installed reports.</span></span> <span data-ttu-id="5227f-109">詳細については、「[Management Studio におけるカスタム レポート](../../ssms/object/custom-reports-in-management-studio.md)」と「[レポート定義スキーマのバージョンを確認する &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5227f-109">For more information, see [Custom Reports in Management Studio](../../ssms/object/custom-reports-in-management-studio.md) and [Find the Report Definition Schema Version &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md).</span></span>  
  
 <span data-ttu-id="5227f-110">レポート作成者は [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="5227f-110">Report authors can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to:</span></span>  
  
-   <span data-ttu-id="5227f-111">マップ レポートのクエリ結果セットから空間データを表示する。</span><span class="sxs-lookup"><span data-stu-id="5227f-111">Visualize spatial data from a query result set for a map report.</span></span> <span data-ttu-id="5227f-112">クエリを実行した後、結果セット ペインの **[空間結果]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="5227f-112">After you run the query, use the **Spatial results** tab in the result set pane.</span></span> <span data-ttu-id="5227f-113">詳細については、「 [オブジェクト エクスプローラーに空間データを表示する方法](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5227f-113">For more information, see [View Spatial Data in Object Explorer](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md).</span></span>  
  
 <span data-ttu-id="5227f-114">ここでは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を使用してさまざまなレポート タスクを実行する操作手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="5227f-114">This section contains step-by-step instructions for performing various reporting tasks using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="5227f-115">共有スケジュールの作成と管理は、レポート マネージャーを使って行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="5227f-115">Creating and managing shared schedules can also be performed using Report Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5227f-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5227f-116">In This Section</span></span>  
  
-   [<span data-ttu-id="5227f-117">Management Studio でレポート サーバーに接続する</span><span class="sxs-lookup"><span data-stu-id="5227f-117">Connect to a Report Server in Management Studio</span></span>](connect-to-a-report-server-in-management-studio.md)  
  
-   [<span data-ttu-id="5227f-118">レポート サーバーのプロパティを設定する (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5227f-118">Set Report Server Properties &#40;Management Studio&#41;</span></span>](set-report-server-properties-management-studio.md)  
  
-   [<span data-ttu-id="5227f-119">ロールを作成、削除、または変更する (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5227f-119">Create, Delete, or Modify a Role &#40;Management Studio&#41;</span></span>](../security/role-definitions-create-delete-or-modify.md)  
  
-   [<span data-ttu-id="5227f-120">アイテムの削除 &#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5227f-120">Delete an Item &#40;Management Studio&#41;</span></span>](delete-an-item-management-studio.md)  
  
-   <span data-ttu-id="5227f-121">[[レポート サーバー ジョブのキャンセル] (Management Studio)](cancel-report-server-jobs-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="5227f-121">[Cancel Report Server Jobs &#40;Management Studio&#41;](cancel-report-server-jobs-management-studio.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5227f-122">参照</span><span class="sxs-lookup"><span data-stu-id="5227f-122">See Also</span></span>  
 <span data-ttu-id="5227f-123">[Management Studio F1 ヘルプのレポートサーバー](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="5227f-123">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="5227f-124">SQL Server Management Studio の概要</span><span class="sxs-lookup"><span data-stu-id="5227f-124">Introducing SQL Server Management Studio</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
  
