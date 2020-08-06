---
title: 'タスク 3 (省略可能): サブスクリプションビューの確認 |Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3f1d3eb7-2baa-4215-b040-0b41e3d10740
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 35cf0c246ab778b46a2ceaa2b6ff6fad02d0b670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632847"
---
# <a name="task-3-optional-reviewing-the-subscription-views"></a><span data-ttu-id="7b7a7-102">タスク 3 (オプション): サブスクリプション ビューを確認する</span><span class="sxs-lookup"><span data-stu-id="7b7a7-102">Task 3 (Optional): Reviewing the Subscription Views</span></span>
  <span data-ttu-id="7b7a7-103">ここでは、SQL ビューが SQL Server Management Studio を使用して作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b7a7-103">In this task, you confirm that the SQL views are created by using SQL Server Management Studio.</span></span>

1.  <span data-ttu-id="7b7a7-104">**SQL Server Management Studio**を起動します。</span><span class="sxs-lookup"><span data-stu-id="7b7a7-104">Launch **SQL Server Management Studio**.</span></span> <span data-ttu-id="7b7a7-105">[**スタート**] ボタンをクリックし、[**すべてのプログラム**]、[ **Microsoft SQL Server 2012**]、[ **SQL Server Management Studio**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b7a7-105">Click the **Start** button, click **All Programs**, click **Microsoft SQL Server 2012**, and then click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="7b7a7-106">[**サーバーへの接続**] ウィンドウで、[**サーバーの種類**] を**データベースエンジン**に設定し、**サーバー名**を入力 (または [ **(ローカル)**] を選択して、適切な**認証**を選択し、[**接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b7a7-106">In the **Connect to Server** window, set **Server Type** to **Database Engine**, type the **server name** (or select **(local)**, and select appropriate **authentication**, and click **Connect**.</span></span>

3.  <span data-ttu-id="7b7a7-107">[**オブジェクトエクスプローラー** ] ウィンドウで、[**データベース**]、[ **MDS**]、[**ビュー**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="7b7a7-107">In the **Object Explorer** pane, expand **Databases**, expand **MDS**, and then expand **Views**.</span></span>

4.  <span data-ttu-id="7b7a7-108">Mdm が表示されていることを確認し**ます。** 一覧の [仕入先] ビュー。</span><span class="sxs-lookup"><span data-stu-id="7b7a7-108">Confirm that you see the **mdm.Suppliers** view in the list.</span></span>

     <span data-ttu-id="7b7a7-109">![SQL Server Management Studio - mdm.Suppliers ビュー](../../2014/tutorials/media/et-reviewingthesubscriptionviews.jpg "SQL Server Management Studio - mdm.Suppliers ビュー")</span><span class="sxs-lookup"><span data-stu-id="7b7a7-109">![SQL Server Management Studio - mdm.Suppliers View](../../2014/tutorials/media/et-reviewingthesubscriptionviews.jpg "SQL Server Management Studio - mdm.Suppliers View")</span></span>

## <a name="next-step"></a><span data-ttu-id="7b7a7-110">次の手順</span><span class="sxs-lookup"><span data-stu-id="7b7a7-110">Next Step</span></span>
 [<span data-ttu-id="7b7a7-111">タスク 4: SQL Server Data Tools を使用して SSIS プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="7b7a7-111">Task 4: Creating an SSIS Project using SQL Server Data Tools</span></span>](../../2014/tutorials/task-4-creating-an-ssis-project-using-sql-server-data-tools.md)