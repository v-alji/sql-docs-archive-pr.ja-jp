---
title: ローカルキューブ (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75f02dd54992e9cc4f94d9845e0e25de5ed988f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643559"
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a><span data-ttu-id="69e77-102">ローカル キューブ (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="69e77-102">Local Cubes (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="69e77-103">ローカル キューブを作成、更新、または削除するには、ASSL スクリプトまたは AMO プログラムを作成して実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69e77-103">To create, update or delete local cubes, you must write and execute either an ASSL script or an AMO program.</span></span>  
  
 <span data-ttu-id="69e77-104">ローカル キューブおよびローカル マイニング モデルは、クライアント ワークステーションがネットワークから切断されている間も分析が可能です。</span><span class="sxs-lookup"><span data-stu-id="69e77-104">Local cubes and local mining models allow analysis on a client workstation while it is disconnected from the network.</span></span> <span data-ttu-id="69e77-105">たとえば、次の図のように、クライアント アプリケーションが OLE DB for OLAP 9.0 Provider (MSOLAP.3) を呼び出すと、このプロバイダーはローカル キューブ エンジンを読み込み、ローカル キューブを作成してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="69e77-105">For example, a client application might call the OLE DB for OLAP 9.0 Provider (MSOLAP.3), which loads the local cube engine to create and query local cubes, as shown in the following illustration:</span></span>  
  
 <span data-ttu-id="69e77-106">![ローカル キューブとローカル モデルのクライアント アーキテクチャ](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "ローカル キューブとローカル モデルのクライアント アーキテクチャ")</span><span class="sxs-lookup"><span data-stu-id="69e77-106">![Client architecture for local cubes and models](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "Client architecture for local cubes and models")</span></span>  
  
 <span data-ttu-id="69e77-107">ADMOD.NET および分析管理オブジェクト (AMO) もまた、ローカル キューブとやり取りするときにローカル キューブ エンジンを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="69e77-107">ADMOD.NET and Analysis Management Objects (AMO) also load the local cube engine when interacting with local cubes.</span></span> <span data-ttu-id="69e77-108">ローカル キューブ エンジンはローカル キューブと接続するときにローカル キューブ ファイルを排他的にロックするため、ローカル キューブ ファイルには同時に 1 つのプロセスしかアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="69e77-108">Only a single process can access a local cube file, because the local cube engine exclusively locks a local cube file when it establishes a connection to the local cube.</span></span> <span data-ttu-id="69e77-109">1 つのプロセスにつき、5 つまでの同時接続が可能です。</span><span class="sxs-lookup"><span data-stu-id="69e77-109">With a process, up to five simultaneous connections are permitted.</span></span>  
  
 <span data-ttu-id="69e77-110">.cub ファイルには、2 つ以上のキューブまたはデータ マイニング モデルが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="69e77-110">A .cub file may contain more than one cube or data mining model.</span></span> <span data-ttu-id="69e77-111">ローカル キューブおよびデータ マイニング モデルに対するクエリは、ローカル キューブ エンジンによって処理されるので、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスへの接続は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="69e77-111">Queries to the local cubes and data mining models are handled by the local cube engine and do not require a connection to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69e77-112">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] をローカル キューブの管理に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="69e77-112">The use of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] to manage local cubes is not supported.</span></span>  
  
## <a name="local-cubes"></a><span data-ttu-id="69e77-113">ローカル キューブ</span><span class="sxs-lookup"><span data-stu-id="69e77-113">Local Cubes</span></span>  
 <span data-ttu-id="69e77-114">ローカルキューブを作成し、インスタンス内の既存のキューブ、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] またはリレーショナルデータソースから設定することができます。</span><span class="sxs-lookup"><span data-stu-id="69e77-114">A local cube can be created and populated from either an existing cube in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance or from a relational data source.</span></span>  
  
|<span data-ttu-id="69e77-115">ローカル キューブ用データのソース</span><span class="sxs-lookup"><span data-stu-id="69e77-115">Source for data for local cube</span></span>|<span data-ttu-id="69e77-116">作成方法</span><span class="sxs-lookup"><span data-stu-id="69e77-116">Creation method</span></span>|  
|------------------------------------|---------------------|  
|<span data-ttu-id="69e77-117">サーバーベースのキューブ</span><span class="sxs-lookup"><span data-stu-id="69e77-117">Server-based cube</span></span>|<span data-ttu-id="69e77-118">CREATE GLOBAL CUBE ステートメントまたは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) スクリプトを使用して、サーバーベースのキューブからキューブを作成および設定できます。</span><span class="sxs-lookup"><span data-stu-id="69e77-118">You can use either the CREATE GLOBAL CUBE statement or an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) script to create and populate a cube from a server-based cube.</span></span> <span data-ttu-id="69e77-119">詳細については、「 [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) 」または「 [Analysis Services スクリプト言語 &#40;Assl&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69e77-119">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) or [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>|  
|<span data-ttu-id="69e77-120">リレーショナルデータソース</span><span class="sxs-lookup"><span data-stu-id="69e77-120">Relational data source</span></span>|<span data-ttu-id="69e77-121">ASSL スクリプトを使用して、OLE DB リレーショナル データベースからキューブを作成して設定します。</span><span class="sxs-lookup"><span data-stu-id="69e77-121">You use an ASSL script to create and populate a cube from an OLE DB relational database.</span></span> <span data-ttu-id="69e77-122">ASSL を使用してローカル キューブを作成するには、ローカル キューブ ファイル (\*.cub) に接続して、サーバー キューブを作成するときに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスで ASSL スクリプトを実行するのと同じ要領で ASSL スクリプトを実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="69e77-122">To create a local cube using ASSL, you simply connect to a local cube file (\*.cub) and execute the ASSL script in the same manner as executing an ASSL script against an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance to create a server cube.</span></span> <span data-ttu-id="69e77-123">詳細については、「 [Analysis Services Scripting Language &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69e77-123">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>|  
  
 <span data-ttu-id="69e77-124">ローカル キューブを再構築してデータを更新するには、REFRESH CUBE ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="69e77-124">Use the REFRESH CUBE statement to rebuild a local cube and update its data.</span></span> <span data-ttu-id="69e77-125">詳細については、「 [REFRESH CUBE ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69e77-125">For more information, see [REFRESH CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube).</span></span>  
  
### <a name="local-cubes-created-from-server-based-cubes"></a><span data-ttu-id="69e77-126">サーバーベースのキューブから作成されたローカル キューブ</span><span class="sxs-lookup"><span data-stu-id="69e77-126">Local Cubes Created from Server-based Cubes</span></span>  
 <span data-ttu-id="69e77-127">サーバーベースのキューブからローカル キューブを作成する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="69e77-127">When creating local cubes created from server-based cubes, the following considerations apply:</span></span>  
  
-   <span data-ttu-id="69e77-128">個別のカウント メジャーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="69e77-128">Distinct count measures are not supported.</span></span>  
  
-   <span data-ttu-id="69e77-129">メジャーを追加する場合は、追加するメジャーに関連するディメンションも最低 1 つ追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69e77-129">When you add a measure, you must also include at least one dimension that is related to the measure being added.</span></span> <span data-ttu-id="69e77-130">メジャーグループに対するディメンションリレーションシップの詳細については、「[ディメンションリレーションシップ](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69e77-130">For more information about dimension relationships to measure groups, see [Dimension Relationships](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
-   <span data-ttu-id="69e77-131">親子階層を追加すると、親子階層のレベルやフィルターは無視されて、親子階層全体が追加されます。</span><span class="sxs-lookup"><span data-stu-id="69e77-131">When you add a parent-child hierarchy, levels and filters on a parent-child hierarchy are ignored and the entire parent-child hierarchy is included.</span></span>  
  
-   <span data-ttu-id="69e77-132">メンバー プロパティは作成されません。</span><span class="sxs-lookup"><span data-stu-id="69e77-132">Member properties are not created.</span></span>  
  
-   <span data-ttu-id="69e77-133">準加法メジャーを含める場合、Account ディメンションおよび Time ディメンションでのスライスは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="69e77-133">When you include a semi-additive measure, no slices are permitted on either the Account or the Time dimension.</span></span>  
  
-   <span data-ttu-id="69e77-134">参照ディメンションは常に具体化されます。</span><span class="sxs-lookup"><span data-stu-id="69e77-134">Reference dimensions are always materialized.</span></span>  
  
-   <span data-ttu-id="69e77-135">多対多ディメンションを含めると、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="69e77-135">When you include a many-to-many dimension, the following rules apply:</span></span>  
  
    -   <span data-ttu-id="69e77-136">多対多ディメンションをスライスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="69e77-136">You cannot slice the many-to-many dimension.</span></span>  
  
    -   <span data-ttu-id="69e77-137">中間メジャー グループのメジャーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69e77-137">You must add a measure from the intermediary measure group.</span></span>  
  
    -   <span data-ttu-id="69e77-138">多対多リレーションシップに関係する 2 つのメジャー グループに共通するディメンションはスライスすることができません。</span><span class="sxs-lookup"><span data-stu-id="69e77-138">You cannot slice any of the dimensions common to the two measure groups involved in the many-to-may relationship.</span></span>  
  
-   <span data-ttu-id="69e77-139">ローカル キューブに追加されたメジャーおよびディメンションに依存する計算されるメンバー、名前付きセット、および割り当てだけがローカル キューブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="69e77-139">Only those calculated members, named sets, and assignments that rely upon measures and dimensions added to the local cube will appear in the local cube.</span></span> <span data-ttu-id="69e77-140">無効な計算されるメンバー、名前付きセット、および割り当ては自動的に除外されます。</span><span class="sxs-lookup"><span data-stu-id="69e77-140">Invalid calculated members, named sets, and assignments will be automatically excluded.</span></span>  
  
### <a name="security"></a><span data-ttu-id="69e77-141">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="69e77-141">Security</span></span>  
 <span data-ttu-id="69e77-142">ユーザーがサーバーキューブからローカルキューブを作成できるようにするには、サーバーキューブに対する**ドリルスルー権限とローカルキューブ**権限がユーザーに与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69e77-142">In order for a user to create a local cube from a server cube, the user must be granted **Drillthrough and Local Cube** permissions on the server cube.</span></span> <span data-ttu-id="69e77-143">詳細については、「 [Grant cube or model permissions &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69e77-143">For more information, see [Grant cube or model permissions &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="69e77-144">ローカル キューブは、サーバー キューブのようにロールを使用してセキュリティで保護されていません。</span><span class="sxs-lookup"><span data-stu-id="69e77-144">Local cubes are not secured using roles like server cubes.</span></span> <span data-ttu-id="69e77-145">ローカル キューブ ファイルへのファイル レベルのアクセス権を持っていれば、ローカル キューブ ファイル内のキューブに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="69e77-145">Anyone with file-level access to a local cube file can query cubes in it.</span></span> <span data-ttu-id="69e77-146">ローカル キューブ ファイルに対して `Encryption Password` 接続プロパティを使用すると、ローカル キューブ ファイルにパスワードを設定できます。</span><span class="sxs-lookup"><span data-stu-id="69e77-146">You can use the `Encryption Password` connection property on a local cube file to set a password on the local cube file.</span></span> <span data-ttu-id="69e77-147">ローカル キューブ ファイルにパスワードを設定すると、以後クエリを実行するためにローカル キューブ ファイルに接続するときにそのパスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="69e77-147">Setting a password on a local cube file requires all future connections to the local cube file to use this password in order to query the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e77-148">参照</span><span class="sxs-lookup"><span data-stu-id="69e77-148">See Also</span></span>  
 <span data-ttu-id="69e77-149">[MDX&#41;&#40;のグローバルキューブステートメントの作成](/sql/mdx/mdx-data-definition-create-global-cube) </span><span class="sxs-lookup"><span data-stu-id="69e77-149">[CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) </span></span>  
 <span data-ttu-id="69e77-150">[Analysis Services スクリプト言語 &#40;ASSL&#41;を使用した開発](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="69e77-150">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 [<span data-ttu-id="69e77-151">MDX&#41;&#40;CUBE ステートメントの更新</span><span class="sxs-lookup"><span data-stu-id="69e77-151">REFRESH CUBE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-refresh-cube)  
  
  
