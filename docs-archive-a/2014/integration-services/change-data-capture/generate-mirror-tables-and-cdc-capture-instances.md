---
title: ミラー テーブルおよび CDC キャプチャ インスタンスの生成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78daea310112cf7e9e78e489097fe9a76e69996b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712302"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a><span data-ttu-id="9b682-102">ミラー テーブルおよび CDC キャプチャ インスタンスの生成</span><span class="sxs-lookup"><span data-stu-id="9b682-102">Generate Mirror Tables and CDC Capture Instances</span></span>
  <span data-ttu-id="9b682-103">[ミラー テーブルの生成] ページを使用すると、CDC インスタンスに含めたテーブルのミラー テーブルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="9b682-103">Use the Generate Mirror Tables page to generate the mirror tables for the tables you included in the CDC instance</span></span>  
  
 <span data-ttu-id="9b682-104">**[実行]** をクリックするとミラー テーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9b682-104">Click **Run** to create the mirror tables.</span></span> <span data-ttu-id="9b682-105">テーブルごとに作成の進行状況が表示され、各ミラー テーブルの作成が正常に終了したか、エラーが発生したかを通知するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b682-105">The progress for the creation of each table is displayed and a message is displayed to let you know whether each mirror table is completed successfully or with errors.</span></span> <span data-ttu-id="9b682-106">エラーが発生した場合は、 **[詳細]** をクリックしてエラーについて説明するダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="9b682-106">If any errors occur, click **Details** to see a dialog box with an explanation of the error.</span></span>  
  
 <span data-ttu-id="9b682-107">テーブルの作成に失敗した場合は、そのまま続行するか、または失敗したテーブルを削除してから続行するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9b682-107">If any of the tables fail to be created, you can choose to continue or delete any tables that failed before continuing.</span></span> <span data-ttu-id="9b682-108">ウィザードの実行が終了したら、Oracle ソース データベースでテーブルを修正するか、CDC インスタンスでそのテーブルを使用しないようにするかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9b682-108">After you finish running the wizard, you can decide whether to fix the table in the Oracle source database or not use it in the CDC instance.</span></span> <span data-ttu-id="9b682-109">テーブルを修正する場合は、 [Edit Tables](edit-tables.md)を行うときにそのテーブルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="9b682-109">If you fix the table, you can add it when you [Edit Tables](edit-tables.md).</span></span>  
  
 <span data-ttu-id="9b682-110">**[次へ]** をクリックして [Finish](finish.md) ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="9b682-110">Click **Next** to open the [Finish](finish.md) page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b682-111">参照</span><span class="sxs-lookup"><span data-stu-id="9b682-111">See Also</span></span>  
 [<span data-ttu-id="9b682-112">SQL Server 変更データベース インスタンスを作成する方法</span><span class="sxs-lookup"><span data-stu-id="9b682-112">How to Create the SQL Server Change Database Instance</span></span>](how-to-create-the-sql-server-change-database-instance.md)  
  
  
