---
title: テーブルの追加 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80c22c992a89ed2cb3db84809b47a7cd08cb514
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643492"
---
# <a name="add-a-table-ssas-tabular"></a><span data-ttu-id="1569c-102">テーブルの追加 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="1569c-102">Add a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="1569c-103">このトピックでは、以前にデータをモデルにインポートしたときのデータ ソースからテーブルを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1569c-103">This topic describes how to add a table from a data source from which you have previously imported data into your model.</span></span> <span data-ttu-id="1569c-104">同じデータ ソースからテーブルを追加するには、既存のデータ ソース接続を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1569c-104">To add a table from the same data source, you can use the existing data source connection.</span></span> <span data-ttu-id="1569c-105">1 つのデータ ソースから任意の数のテーブルをインポートする場合は、常に 1 つの接続を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1569c-105">It is recommended you always use a single connection when importing any number of tables from a single data source.</span></span>  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a><span data-ttu-id="1569c-106">既存のデータ ソースからテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="1569c-106">To add a table from an existing data source</span></span>  
  
1.  <span data-ttu-id="1569c-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックしてから **[既存の接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1569c-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="1569c-108">**[既存の接続]** ページで、追加するテーブルが含まれているデータ ソースへの接続を選択し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1569c-108">On the **Existing Connections** page, select the connection to the data source that has the table you want to add, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="1569c-109">**[テーブルとビューの選択]** ページで、データ ソースからモデルに追加するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="1569c-109">On the **Select Tables and Views** page, select the table from the data source you want to add to your model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1569c-110">**[テーブルとビューの選択]** ページには、以前にインポートされたテーブルは選択済みとして表示されません。</span><span class="sxs-lookup"><span data-stu-id="1569c-110">The **Select Tables and Views** page will not show tables that were previously imported as checked.</span></span>  <span data-ttu-id="1569c-111">この接続を使用して以前にインポートされたテーブルを選択し、そのテーブルに別の表示名を指定しなかった場合は、表示名に 1 が付加されます。</span><span class="sxs-lookup"><span data-stu-id="1569c-111">If you select a table that was previously imported using this connection, and you did not give the table a different friendly name, a 1 will be appended to the friendly name.</span></span> <span data-ttu-id="1569c-112">この接続を使用して以前にインポートされたテーブルを再度選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1569c-112">You do not need to re-select any tables that were previously imported by using this connection.</span></span>  
  
4.  <span data-ttu-id="1569c-113">必要に応じて、**[プレビューとフィルター]** を使用して、特定の列のみを選択するか、インポートするデータにフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="1569c-113">If necessary, use **Preview & Filter** to select only certain columns or apply filters to the data to be imported.</span></span>  
  
5.  <span data-ttu-id="1569c-114">**[完了]** をクリックして、新しいテーブルをインポートします。</span><span class="sxs-lookup"><span data-stu-id="1569c-114">Click **Finish** to import the new table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1569c-115">1 つのデータ ソースから複数のテーブルを同時にインポートする場合、それらのテーブル間のソースでのリレーションシップがモデル内に自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="1569c-115">When importing multiple tables at the same time from a single data source, any relationships between those tables at the source will automatically be created in the model.</span></span> <span data-ttu-id="1569c-116">ただし、後からテーブルを追加する場合は、新しく追加されたテーブルと以前にインポートされたテーブルの間のリレーションシップを、モデル内に手動で作成することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="1569c-116">When adding a table later; however, you may need to manually create relationships in the model between newly added tables and the tables that were previously imported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1569c-117">参照</span><span class="sxs-lookup"><span data-stu-id="1569c-117">See Also</span></span>  
 <span data-ttu-id="1569c-118">[SSAS 表形式&#41;&#40;データをインポートする](../import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="1569c-118">[Import Data &#40;SSAS Tabular&#41;](../import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="1569c-119">テーブルの削除 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="1569c-119">Delete a Table &#40;SSAS Tabular&#41;</span></span>](delete-a-table-ssas-tabular.md)  
  
  
