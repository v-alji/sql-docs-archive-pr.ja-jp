---
title: データソースビューおよびデータソースへの変更の管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data sources
- modifying data source views
- data source views [Analysis Services], schema updates
- data sources [Analysis Services], schema updates
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f558ce6aaf9e57576d5773322352d33b81a3392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714649"
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a><span data-ttu-id="d8ee4-102">データ ソース ビューおよびデータ ソースへの変更の管理</span><span class="sxs-lookup"><span data-stu-id="d8ee4-102">Manage Changes to Data Source Views and Data Sources</span></span>
  <span data-ttu-id="d8ee4-103">スキーマ生成ウィザードが再実行されると、元の生成に使用されたものと同じデータ ソースとデータ ソース ビューが再び使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-103">When the Schema Generation Wizard is rerun, it reuses the same data source and data source view that it used for the original generation.</span></span> <span data-ttu-id="d8ee4-104">データ ソースまたはデータ ソース ビューを追加しても、ウィザードでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-104">If you add a data source or a data source view, the wizard does not use it.</span></span> <span data-ttu-id="d8ee4-105">最初の生成後に元のデータ ソースまたはデータ ソース ビューを削除した場合は、最初からウィザードを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-105">If you delete the original data source or data source view after the initial generation, you must run the wizard from the beginning.</span></span> <span data-ttu-id="d8ee4-106">ウィザードで以前使用した設定もすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-106">All previous settings in the wizard are also deleted.</span></span> <span data-ttu-id="d8ee4-107">削除されたデータ ソースまたはデータ ソース ビューにバインドされていた、基になるデータベースの既存のオブジェクトは、次にスキーマ生成ウィザードを実行したとき、ユーザーが作成したオブジェクトとして取り扱われます。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-107">Any existing objects in an underlying database that were bound to a deleted data source or data source view are treated as user-created objects the next time you run the Schema Generation Wizard.</span></span>  
  
 <span data-ttu-id="d8ee4-108">データ ソース ビューに、基になるデータベースの生成時の実際の状態が反映されていないと、スキーマ生成ウィザードではサブジェクト領域データベースのスキーマを生成するときにエラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-108">If the data source view does not reflect the actual state of the underlying database at the time of generation, the Schema Generation Wizard may encounter errors when it generates the schema for the subject area database.</span></span> <span data-ttu-id="d8ee4-109">たとえば、データ ソース ビューで列のデータ型が **int**に指定されているときに、この列のデータ型が実際には **string**である場合、スキーマ生成ウィザードではデータ ソース ビューに合わせて外部キーのデータ型を **INT** に設定します。リレーションシップを作成すると、実際のデータ型が **string**であるため、処理は失敗します。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-109">For example, if the data source view specifies that the data type for a column is **int**, but data type for the column is actually **string**, the Schema Generation Wizard sets the data type for the foreign key to **INT** to match the data source view and then fails when it creates the relationship because the actual type is **string**.</span></span>  
  
 <span data-ttu-id="d8ee4-110">一方、データ ソース接続文字列を以前の生成後に別のデータベースに変更した場合は、エラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-110">On the other hand, if you change the data source connection string to a different database from the previous generation, no error is generated.</span></span> <span data-ttu-id="d8ee4-111">この場合は新しいデータベースが使用され、以前のデータベースには変更は行われません。</span><span class="sxs-lookup"><span data-stu-id="d8ee4-111">The new database is used, and no change is made to the previous database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ee4-112">参照</span><span class="sxs-lookup"><span data-stu-id="d8ee4-112">See Also</span></span>  
 [<span data-ttu-id="d8ee4-113">増分生成の理解</span><span class="sxs-lookup"><span data-stu-id="d8ee4-113">Understanding Incremental Generation</span></span>](understanding-incremental-generation.md)  
  
  
