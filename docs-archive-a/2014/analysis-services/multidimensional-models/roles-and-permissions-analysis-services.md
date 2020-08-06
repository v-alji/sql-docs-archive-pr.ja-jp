---
title: ロールと権限 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6595d931b2c2760e5fd3013ff6bec88f85106d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743542"
---
# <a name="roles-and-permissions-analysis-services"></a><span data-ttu-id="2c042-102">ロールと権限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2c042-102">Roles and Permissions (Analysis Services)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="2c042-103">には、操作、オブジェクト、およびデータへのアクセスを許可する、ロールベースの承認モデルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c042-103">provides a role-based authorization model that grants access to operations, objects, and data.</span></span> <span data-ttu-id="2c042-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスまたはデータベースにアクセスするすべてのユーザーは、ロールのコンテキスト内でアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c042-104">All users who access an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance or database must do so within the context of a role.</span></span>  
  
 <span data-ttu-id="2c042-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] システム管理者は、サーバーでの操作への無制限のアクセスが許可される **サーバー管理者ロール** へのメンバーシップの付与を担当します。</span><span class="sxs-lookup"><span data-stu-id="2c042-105">As an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] system administrator, you are in charge of granting membership to the **server administrator role** that conveys unrestricted access to operations on the server.</span></span> <span data-ttu-id="2c042-106">このロールの権限は固定されており、カスタマイズできません。</span><span class="sxs-lookup"><span data-stu-id="2c042-106">This role has fixed permissions and cannot be customized.</span></span> <span data-ttu-id="2c042-107">既定では、ローカルの Administrators グループのメンバーは、自動的に Analysis Services システム管理者になります。</span><span class="sxs-lookup"><span data-stu-id="2c042-107">By default, members of the local Administrators group are automatically Analysis Services system administrators.</span></span>  
  
 <span data-ttu-id="2c042-108">データのクエリまたは処理を行う管理者以外のユーザーには、 **データベース ロール**によってアクセス権が付与されます。</span><span class="sxs-lookup"><span data-stu-id="2c042-108">Non-administrative users who query or process data are granted access through **database roles**.</span></span> <span data-ttu-id="2c042-109">システム管理者もデータベース管理者も、特定のデータベースでの異なるレベルのアクセスに対応するロールを作成し、アクセスを要するすべてのユーザーにメンバーシップを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="2c042-109">Both system administrators and database administrators can create the roles that describe different levels of access within a given database, and then assign membership to every user who requires access.</span></span> <span data-ttu-id="2c042-110">各ロールには、特定のデータベース内のオブジェクトおよび操作にアクセスするための、カスタマイズされた一連の権限があります。</span><span class="sxs-lookup"><span data-stu-id="2c042-110">Each role has a customized set of permissions for accessing objects and operations within a particular database.</span></span> <span data-ttu-id="2c042-111">権限を割り当てられるレベルは、データベース、キューブやディメンションなどの内部オブジェクト (パースペクティブを除く)、および行です。</span><span class="sxs-lookup"><span data-stu-id="2c042-111">You can assign permissions at these levels: database, interior objects such as cubes and dimensions (but not perspectives), and rows.</span></span>  
  
 <span data-ttu-id="2c042-112">ロールの作成とメンバーシップの割り当ては、別の操作として行うのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="2c042-112">It is common practice to create roles and assign membership as separate operations.</span></span> <span data-ttu-id="2c042-113">多くの場合、モデル デザイナーは、デザイン フェーズ中にロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c042-113">Often, the model designer adds roles during the design phase.</span></span> <span data-ttu-id="2c042-114">この方法で、すべてのロールの定義は、モデルを定義するプロジェクト ファイルに反映されます。</span><span class="sxs-lookup"><span data-stu-id="2c042-114">This way, all role definitions are reflected in the project files that define the model.</span></span> <span data-ttu-id="2c042-115">ロールのメンバーシップは、一般的には後でデータベースが実際に運用されるときに設定されます。通常は、データベース管理者が独立した操作として開発、テスト、および実行できるスクリプトを作成して設定します。</span><span class="sxs-lookup"><span data-stu-id="2c042-115">Role membership is typically rolled out later as the database moves into production, usually by database administrators who create scripts that can be developed, tested, and run as an independent operation.</span></span>  
  
 <span data-ttu-id="2c042-116">すべての承認は、有効な Windows ユーザー ID を前提としています。</span><span class="sxs-lookup"><span data-stu-id="2c042-116">All authorization is predicated on a valid Windows user identity.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="2c042-117">は、ユーザー ID の認証に Windows 認証だけを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c042-117">uses Windows authentication exclusively to authenticate user identities.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="2c042-118">は、独自の認証メソッドをサポートしません。「 [Analysis Services でサポートされる認証方法](../instances/authentication-methodologies-supported-by-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c042-118">provides no proprietary authentication method.See [Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2c042-119">権限は、データベース内のすべてのロールにわたって、Windows ユーザーまたはグループごとに加算的です。</span><span class="sxs-lookup"><span data-stu-id="2c042-119">Permissions are additive for each Windows user or group, across all roles in the database.</span></span> <span data-ttu-id="2c042-120">1 つのロールで、あるユーザーまたはグループに対して特定のタスクの実行や、特定のデータの表示の権限を拒否しても、別のロールでこれらの権限がそのユーザーまたはグループに与えられる場合、ユーザーまたはグループはそのタスクの実行またはデータの表示の権限を持つことになります。</span><span class="sxs-lookup"><span data-stu-id="2c042-120">If one role denies a user or group permission to perform certain tasks or view certain data, but another role grants this permission to that user or group, the user or group will have permission to perform the task or view the data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c042-121">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2c042-121">In this section</span></span>  
  
-   [<span data-ttu-id="2c042-122">オブジェクトと操作へのアクセスの承認 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-122">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-123">データベース権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-123">Grant database permissions &#40;Analysis Services&#41;</span></span>](grant-database-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-124">キューブ権限またはモデル権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-124">Grant cube or model permissions &#40;Analysis Services&#41;</span></span>](grant-cube-or-model-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-125">処理権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-125">Grant process permissions &#40;Analysis Services&#41;</span></span>](grant-process-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-126">オブジェクト メタデータに対する定義の読み取り権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-126">Grant read definition permissions on object metadata &#40;Analysis Services&#41;</span></span>](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-127">データ ソース オブジェクトに対する権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-127">Grant permissions on a data source object &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-128">データ マイニング構造およびデータ マイニング モデルに対する権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-128">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-129">ディメンションに対する権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-129">Grant permissions on a dimension &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-130">ディメンション データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-130">Grant custom access to dimension data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [<span data-ttu-id="2c042-131">セル データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-131">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c042-132">参照</span><span class="sxs-lookup"><span data-stu-id="2c042-132">See Also</span></span>  
 [<span data-ttu-id="2c042-133">ロールの作成および管理 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="2c042-133">Create and Manage Roles &#40;SSAS Tabular&#41;</span></span>](../tabular-models/roles-ssas-tabular.md)  
  
  
