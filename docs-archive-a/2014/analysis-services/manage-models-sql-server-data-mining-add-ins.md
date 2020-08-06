---
title: モデルの管理 (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5f4b5961ec79bb949bf7fa5f53a980f066e81379
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643595"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a><span data-ttu-id="8c11a-102">モデルの管理 (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="8c11a-102">Manage Models (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="8c11a-103">![[データ マイニング] リボンの [モデルの管理] ボタン](media/dmc-manage.gif "[データ マイニング] リボンの [モデルの管理] ボタン")</span><span class="sxs-lookup"><span data-stu-id="8c11a-103">![Manage Models button, Data Mining ribbon](media/dmc-manage.gif "Manage Models button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="8c11a-104">[**モデルの管理**] ダイアログボックスを使用すると、現在接続しているサーバーに格納されている既存のマイニングモデルとマイニング構造を操作でき [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8c11a-104">The **Manage Models** dialog box enables you to interact with existing mining models and mining structures that are stored in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server to which you are currently connected.</span></span> <span data-ttu-id="8c11a-105">さらに、現在のセッション中に作成された一時的な構造およびモデルを表示および管理できます。</span><span class="sxs-lookup"><span data-stu-id="8c11a-105">You can also view and manage temporary structures and models that have been created during the current session.</span></span> <span data-ttu-id="8c11a-106">セッション モデルおよびサーバー上に格納されているモデルをこれまでに使用している場合、ダイアログ ボックスにこれらのモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c11a-106">If you have used both session models and models stored on a server, both are visible in the dialog box.</span></span>  
  
## <a name="using-the-manage-models-wizard"></a><span data-ttu-id="8c11a-107">モデルの管理ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="8c11a-107">Using the Manage Models Wizard</span></span>  
 <span data-ttu-id="8c11a-108">[モデルの**管理**] をクリックすると、[**マイニング構造とマイニングモデルの管理**] ダイアログボックスが開き、既存のデータマイニングモデルおよび構造を管理するための次の機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8c11a-108">When you click **Manage Models**, the **Manage Mining Structures and Models** dialog box opens, providing access to the following functionality for managing existing data mining models and structures:</span></span>  
  
-   <span data-ttu-id="8c11a-109">マイニング モデルまたは構造の名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="8c11a-109">Rename a mining model or structure</span></span>  
  
-   <span data-ttu-id="8c11a-110">マイニング モデルまたは構造を削除する。</span><span class="sxs-lookup"><span data-stu-id="8c11a-110">Delete a mining model or structure</span></span>  
  
-   <span data-ttu-id="8c11a-111">マイニング モデルまたは構造を消去する。</span><span class="sxs-lookup"><span data-stu-id="8c11a-111">Clear a mining model or structure</span></span>  
  
-   <span data-ttu-id="8c11a-112">新しいデータまたは既存のデータを使用してマイニング構造を処理する。</span><span class="sxs-lookup"><span data-stu-id="8c11a-112">Process a mining structure, using either new or existing data</span></span>  
  
-   <span data-ttu-id="8c11a-113">マイニング モデルまたは構造をエクスポートまたはインポートする。</span><span class="sxs-lookup"><span data-stu-id="8c11a-113">Export or import a mining model or structure</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c11a-114">このダイアログ ボックスを使用してクエリまたはモデルを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="8c11a-114">You cannot create queries or models by using this dialog box.</span></span> <span data-ttu-id="8c11a-115">新しいマイニング構造を作成するには、Excel 用のデータマイニングクライアントに用意されているウィザードのいずれかを使用するか、**詳細エディターデータマイニングクエリ**を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c11a-115">To create a new mining structure, use one of the wizards provided in the Data Mining Client for Excel, or use the **Data Mining Query Advanced Editor**.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="8c11a-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="8c11a-116">Requirements</span></span>  
 <span data-ttu-id="8c11a-117">データ マイニング モデルを管理するには、最初に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c11a-117">To manage data mining models, you must first create a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8c11a-118">一時ファイルに保存されているセッション モデルを操作する場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="8c11a-118">A connection is required even if you are working with session models stored in a temporary file.</span></span> <span data-ttu-id="8c11a-119">接続を作成または変更する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c11a-119">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="8c11a-120">接続先の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに既存のデータ マイニング構造またはデータ マイニング モデルがない場合は、ウィザードまたはこのアドインに用意されているその他のツールを使用して、データ マイニング構造またはデータ マイニング モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8c11a-120">If the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you connect to does not contain any existing data mining structures or data mining models, you can create them by using the wizards and other tools provided by this add-in.</span></span> <span data-ttu-id="8c11a-121">**詳細エディターのデータマイニングモデル**を使用して新しいモデルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8c11a-121">You can also create new models by using the **Data Mining Model Advanced Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c11a-122">参照</span><span class="sxs-lookup"><span data-stu-id="8c11a-122">See Also</span></span>  
 <span data-ttu-id="8c11a-123">[Excel 用データマイニングアドイン &#40;マイニングモデルのドキュメント化&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="8c11a-123">[Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="8c11a-124">Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="8c11a-124">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
