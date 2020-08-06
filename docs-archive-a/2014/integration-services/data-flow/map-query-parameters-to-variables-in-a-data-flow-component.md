---
title: クエリ パラメーターをデータ フロー コンポーネントの変数にマップする | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b38940313397c7be7a8bcdbd2bf7f5233583096e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741149"
---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a><span data-ttu-id="4e76f-102">クエリ パラメーターをデータ フロー コンポーネントの変数にマップする</span><span class="sxs-lookup"><span data-stu-id="4e76f-102">Map Query Parameters to Variables in a Data Flow Component</span></span>
  <span data-ttu-id="4e76f-103">パラメーター化クエリを使用するように OLE DB ソースを構成すると、パラメーターを変数にマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="4e76f-103">When you configure the OLE DB source to use parameterized queries, you can map the parameters to variables.</span></span>  
  
 <span data-ttu-id="4e76f-104">OLE DB ソースは、データ ソースに接続する際に、パラメーター化クエリを使用してデータのフィルター選択を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4e76f-104">The OLE DB source uses parameterized queries to filter data when the source connects to a data source.</span></span>  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a><span data-ttu-id="4e76f-105">クエリ パラメーターを変数にマップするには</span><span class="sxs-lookup"><span data-stu-id="4e76f-105">To map a query parameter to a variable</span></span>  
  
1.  <span data-ttu-id="4e76f-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4e76f-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="4e76f-107">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="4e76f-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="4e76f-108">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、OLE DB ソースをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4e76f-108">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.</span></span>  
  
4.  <span data-ttu-id="4e76f-109">OLE DB ソースを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e76f-109">Right-click the OLE DB source, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="4e76f-110">**[OLE DB ソース エディター]** で、OLE DB 接続マネージャーを選択してデータ ソースへの接続に使用するか、 **[新規作成]** をクリックして新しい OLE DB 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e76f-110">In the **OLE DB Source Editor**, select an OLE DB connection manager to use to connect to the data source, or click **New** to create a new OLE DB connection manager.</span></span>  
  
6.  <span data-ttu-id="4e76f-111">データ アクセス モードの **[SQL コマンド]** オプションをクリックし、 **[SQL コマンド テキスト]** ペインにパラメーター化クエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="4e76f-111">Select the **SQL command** option for data access mode, and then type a parameterized query in the **SQL command text** pane.</span></span>  
  
7.  <span data-ttu-id="4e76f-112">**[パラメーター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e76f-112">Click **Parameters**.</span></span>  
  
8.  <span data-ttu-id="4e76f-113">**[クエリ パラメーターの設定]** ダイアログ ボックスで、 **[パラメーター]** 一覧にある各パラメーターを、 **[変数]** 一覧の変数にマップするか、 **[\<New variable>]** をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="4e76f-113">In the **Set Query Parameters** dialog box, map each parameter in the **Parameters** list to a variable in the **Variables** list, or create a new variable by clicking **\<New variable>**.</span></span> <span data-ttu-id="4e76f-114">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e76f-114">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4e76f-115">マッピングで使用できる変数は、パッケージのスコープ内、Foreach ループなどの親コンテナーのスコープ内、またはデータ フロー コンポーネントが含まれるデータ フロー タスクのスコープ内にある、システム変数およびユーザー定義変数だけです。</span><span class="sxs-lookup"><span data-stu-id="4e76f-115">Only system variables and user-defined variables that are in the scope of the package, a parent container such as a Foreach Loop, or the Data Flow task that contains the data flow component are available for mapping.</span></span> <span data-ttu-id="4e76f-116">変数のデータ型は、パラメーターが割り当てられる WHERE 句の列と互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e76f-116">The variable must have a data type that is compatible with the column in the WHERE clause to which the parameter is assigned.</span></span>  
  
9. <span data-ttu-id="4e76f-117">**[プレビュー]** をクリックすると、クエリが返すデータを最大 200 行表示できます。</span><span class="sxs-lookup"><span data-stu-id="4e76f-117">You can click **Preview** to view up to 200 rows of the data that the query returns.</span></span>  
  
10. <span data-ttu-id="4e76f-118">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e76f-118">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e76f-119">参照</span><span class="sxs-lookup"><span data-stu-id="4e76f-119">See Also</span></span>  
 <span data-ttu-id="4e76f-120">[OLE DB ソース](ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="4e76f-120">[OLE DB Source](ole-db-source.md) </span></span>  
 [<span data-ttu-id="4e76f-121">参照変換</span><span class="sxs-lookup"><span data-stu-id="4e76f-121">Lookup Transformation</span></span>](transformations/lookup-transformation.md)  
  
  
