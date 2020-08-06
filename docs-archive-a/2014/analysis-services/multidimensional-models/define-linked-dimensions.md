---
title: リンクディメンションの定義 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: d5ad5eae-5dde-46a6-91c3-c8766d016dec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 088dda52042a53c252eed8d759e54af4dee1a029
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712565"
---
# <a name="define-linked-dimensions"></a><span data-ttu-id="6caa8-102">リンク ディメンションの定義</span><span class="sxs-lookup"><span data-stu-id="6caa8-102">Define Linked Dimensions</span></span>
  <span data-ttu-id="6caa8-103">リンク ディメンションは、バージョンと互換性レベルが同じである別の Analysis Services データベース内で作成および保存されたディメンションに基づいています。</span><span class="sxs-lookup"><span data-stu-id="6caa8-103">A linked dimension is based on a dimension created and stored in another Analysis Services database of the same version and compatibility level.</span></span> <span data-ttu-id="6caa8-104">リンク ディメンションを使用すると、1 つのデータベースでディメンションを作成、保存、保守することができ、さらにそのディメンションを複数のデータベースで使用可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-104">By using a linked dimension, you can create, store, and maintain a dimension on one database, while making it available to users of multiple databases.</span></span> <span data-ttu-id="6caa8-105">ユーザーに対しては、リンク ディメンションは他のディメンションと同様に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-105">To users, a linked dimension appears like any other dimension.</span></span>  
  
 <span data-ttu-id="6caa8-106">リンク ディメンションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="6caa8-106">Linked dimensions are read-only.</span></span> <span data-ttu-id="6caa8-107">ディメンションを変更するか、新しいリレーションシップを作成するには、ソース ディメンションを変更し、次にリンク ディメンションとそのリレーションシップを削除して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6caa8-107">If you want to modify the dimension or create new relationships, you must change the source dimension, then delete and recreate the linked dimension and its relationships.</span></span> <span data-ttu-id="6caa8-108">ソース オブジェクトから変更を取得する目的で、リンク ディメンションを更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="6caa8-108">You cannot refresh a linked dimension to pick up changes from the source object.</span></span>  
  
 <span data-ttu-id="6caa8-109">関連するすべてのメジャー グループおよびディメンションは同じソース データベースから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6caa8-109">All related measure groups and dimensions must come from the same source database.</span></span> <span data-ttu-id="6caa8-110">キューブに追加したローカル メジャー グループとリンク ディメンションの間で新しいリレーションシップを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="6caa8-110">You cannot create new relationships between local measure groups and the linked dimensions you add to your cube.</span></span> <span data-ttu-id="6caa8-111">リンク ディメンションおよびメジャー グループを現在のキューブに追加した後、両者間のリレーションシップがソース データベース内で維持される必要があります。</span><span class="sxs-lookup"><span data-stu-id="6caa8-111">After linked dimensions and measure groups have been added to the current cube, the relationships between them must be maintained in their source database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6caa8-112">更新機能が利用できないため、ほとんどの Analysis Services 開発者は、ディメンションをリンクする代わりにディメンションをコピーします。</span><span class="sxs-lookup"><span data-stu-id="6caa8-112">Because refresh is not available, most Analysis Services developers copy dimensions rather than link them.</span></span> <span data-ttu-id="6caa8-113">同じソリューション内にある複数のプロジェクトに対してソリューションをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-113">You can copy dimensions across projects within the same solution.</span></span> <span data-ttu-id="6caa8-114">詳細については、「 [SSAS 内でのリンク ディメンションの更新](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6caa8-114">For more information, see [Refresh of a linked dimension in SSAS](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6caa8-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="6caa8-115">Prerequisites</span></span>  
 <span data-ttu-id="6caa8-116">ディメンションを提供するソース データベースとそれを使用する現在のデータベースは、同じバージョンと互換性レベルとする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6caa8-116">The source database that provides the dimension and the current database that uses it must be at the same version and compatibility level.</span></span> <span data-ttu-id="6caa8-117">詳細については、「[多次元データベースの互換性レベルを設定する &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6caa8-117">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).</span></span>  
  
 <span data-ttu-id="6caa8-118">ソース データベースを配置してオンラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6caa8-118">The source database must be deployed and online.</span></span> <span data-ttu-id="6caa8-119">リンク オブジェクトをパブリッシュまたは使用するサーバーは、操作ができるように構成する必要があります (以下の説明を参照)。</span><span class="sxs-lookup"><span data-stu-id="6caa8-119">Servers that publish or consume linked objects must be configured to allow the operation (see below).</span></span>  
  
 <span data-ttu-id="6caa8-120">使用するディメンション自体をリンク ディメンションにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6caa8-120">The dimension you want to use cannot itself be a linked dimension.</span></span>  
  
## <a name="configure-server-to-allow-linked-objects"></a><span data-ttu-id="6caa8-121">リンク オブジェクトを許可するサーバーの構成</span><span class="sxs-lookup"><span data-stu-id="6caa8-121">Configure server to allow linked objects</span></span>  
  
1.  <span data-ttu-id="6caa8-122">SQL Server Management Studio で Analysis Services サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-122">In SQL Server Management Studio, connect to an Analysis Services server.</span></span> <span data-ttu-id="6caa8-123">オブジェクト エクスプローラーでサーバー名を右クリックし、 **[ファセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6caa8-123">In Object Explorer, right-click the server name and select **Facets**.</span></span>  
  
2.  <span data-ttu-id="6caa8-124">**LinkedObjectsLinksFromOtherInstancesEnabled** を **True** に設定し、他のインスタンスで実行されるデータベース内に格納されたリンク オブジェクトに対してサーバーで要求を発行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6caa8-124">Set **LinkedObjectsLinksFromOtherInstancesEnabled** to **True** to allow the server to issue requests for linked objects that reside in databases running on other instances.</span></span>  
  
3.  <span data-ttu-id="6caa8-125">**LinkedObjectsLinksToOtherInstances** を **True** に設定し、他のインスタンスで実行されるデータベースのリンク オブジェクトに対してサーバーでデータを要求できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6caa8-125">Set **LinkedObjectsLinksToOtherInstances** to **True** to allow the server to request data for linked on databases running on other instances.</span></span>  
  
## <a name="create-a-linked-dimension-in-sql-server-data-tools"></a><span data-ttu-id="6caa8-126">SQL Server データ ツールでリンク ディメンションを作成するには</span><span class="sxs-lookup"><span data-stu-id="6caa8-126">Create a linked dimension in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="6caa8-127">ウィザードを開始します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-127">Start the wizard.</span></span> <span data-ttu-id="6caa8-128">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **データベースまたはプロジェクトの** [ディメンション] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] フォルダーを右クリックし、 **[新しいリンク ディメンション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6caa8-128">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **Dimensions** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project, and then click **New Linked Dimension**.</span></span>  
  
2.  <span data-ttu-id="6caa8-129">ディメンションを提供する Analysis Services データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-129">Connect to the Analysis Services database that provides the dimension.</span></span> <span data-ttu-id="6caa8-130">リンク オブジェクト ウィザードの **[データ ソースの選択]** ページで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースを選択するか、新しいデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-130">On the **Select a Data Source** page of the Linked Object Wizard, choose the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source or create a new one.</span></span>  
  
3.  <span data-ttu-id="6caa8-131">ウィザードの **[オブジェクトの選択]** ページで、リモート データベース内でリンクするディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-131">On the **Select Objects** page of the wizard, choose the dimensions you want to link to in the remote database.</span></span>  
  
4.  <span data-ttu-id="6caa8-132">**[ウィザードの完了]** ページで、リンク オブジェクトをプレビューできます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-132">On the **Completing the Wizard** page, you can preview the linked objects.</span></span> <span data-ttu-id="6caa8-133">既に存在するディメンションと同じ名前のディメンションにリンクした場合は、序数 (最初の重複名の "1" から始まる数) が名前に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-133">If you link a dimension that has the same name as one that already exists, an ordinal number (starting with '1' for the first duplicated name) is appended to the name.</span></span> <span data-ttu-id="6caa8-134">ウィザードを完了すると、ディメンションが **[ディメンション]** フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-134">When you complete the wizard, the dimension is added to the **Dimensions** folder.</span></span>  
  
##  <a name="create-a-new-data-source-connection-to-an-analysis-services-database"></a><a name="bkmk_CreateNew"></a><span data-ttu-id="6caa8-135">Analysis Services データベースへの新しいデータソース接続の作成</span><span class="sxs-lookup"><span data-stu-id="6caa8-135">Create a New Data Source Connection to an Analysis Services Database</span></span>  
 <span data-ttu-id="6caa8-136">新しいデータ ソース ウィザードを使用して、ディメンションを提供する Analysis Services データベースに関するプロジェクト接続情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-136">Use the New Data Source wizard to add to your project connection information about the Analysis Services database that provides the dimension.</span></span> <span data-ttu-id="6caa8-137">リンク オブジェクト ウィザードの [データ ソースの選択] ページにある **[新しいデータ ソース]** をクリックしてウィザードを起動できます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-137">You can start the wizard by clicking **New Data Source** in the Select a Data Source page of the Linked Objects wizard.</span></span>  
  
1.  <span data-ttu-id="6caa8-138">データ ソース ウィザードの [接続の定義方法を選択します] ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6caa8-138">In the Data Source Wizard, on the Select how to define the connection page, click **New**.</span></span>  
  
2.  <span data-ttu-id="6caa8-139">接続マネージャーで、プロバイダーが **[ネイティブ OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-139">In Connection Manager, verify that the provider is set to **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.</span></span>  
  
3.  <span data-ttu-id="6caa8-140">サーバーの名前 ( *servername* \\ 名前付きインスタンスの場合は servername*instancename*を使用)<sup>1</sup>を入力するか、 **localhost**と入力して、同じコンピューター上で実行されている Analysis Services サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-140">Enter the name of the server (use *servername*\\*instancename* for a named instance)<sup>1</sup> or type **localhost** to connect to an Analysis Services server that is running on the same computer.</span></span>  
  
4.  <span data-ttu-id="6caa8-141">接続には Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-141">Use Windows authentication for the connection.</span></span>  
  
5.  <span data-ttu-id="6caa8-142">**[初期カタログ]** の下矢印をクリックしてこのサーバーのデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-142">In **Initial catalog**, click the down arrow to select a database on this server.</span></span>  
  
6.  <span data-ttu-id="6caa8-143">データ ソース ウィザードで **[次へ]** をクリックして次に進みます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-143">On the Data Source Wizard, click **Next** to continue.</span></span>  
  
7.  <span data-ttu-id="6caa8-144">[権限借用情報] ページで、 **[サービス アカウントを使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6caa8-144">On the Impersonation Information page, click **Use the service account**.</span></span> <span data-ttu-id="6caa8-145">**[次へ]** をクリックし、ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="6caa8-145">Click **Next**, and then finish the wizard.</span></span> <span data-ttu-id="6caa8-146">リンク オブジェクト ウィザードでは、ここで定義した接続が選択されます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-146">The connection you just defined will be selected in the Linked Objects Wizard.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6caa8-147">次の手順</span><span class="sxs-lookup"><span data-stu-id="6caa8-147">Next Steps</span></span>  
 <span data-ttu-id="6caa8-148">リンク ディメンションの構造は変更できないので、ディメンション デザイナーの **[ディメンション構造]** タブではリンク ディメンションの構造を表示できません。</span><span class="sxs-lookup"><span data-stu-id="6caa8-148">You cannot change the structure of a linked dimension, so you cannot view it with the **Dimension Structure** tab of Dimension Designer.</span></span> <span data-ttu-id="6caa8-149">リンクディメンションを処理すると、[**ブラウザー** ] タブで表示できます。名前を変更したり、名前の翻訳を作成したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6caa8-149">After processing the linked dimension, you can view it with the **Browser** tab. You can also change its name and create a translation for the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6caa8-150">参照</span><span class="sxs-lookup"><span data-stu-id="6caa8-150">See Also</span></span>  
 <span data-ttu-id="6caa8-151">[多次元データベースの互換性レベルを設定する &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="6caa8-151">[Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md) </span></span>  
 <span data-ttu-id="6caa8-152">[リンクメジャーグループ](linked-measure-groups.md) </span><span class="sxs-lookup"><span data-stu-id="6caa8-152">[Linked Measure Groups](linked-measure-groups.md) </span></span>  
 [<span data-ttu-id="6caa8-153">ディメンション リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="6caa8-153">Dimension Relationships</span></span>](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
