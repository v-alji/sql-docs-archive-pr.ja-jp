---
title: セキュリティロール (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], roles
- Analysis Services objects, roles
- security [Analysis Services], roles
- roles [Analysis Services], about roles
- server roles [Analysis Services]
- database roles [Analysis Services]
- roles [Analysis Services]
- storing data [Analysis Services], roles
- access rights [Analysis Services], roles
ms.assetid: 5b7e9cef-ff68-4d8e-99bc-e0094ced1baa
author: minewiskan
ms.author: owend
ms.openlocfilehash: e62abaab5a8f74dfee7d51962f2fb243dc6eb20a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736978"
---
# <a name="security-roles--analysis-services---multidimensional-data"></a><span data-ttu-id="710cf-102">セキュリティ ロール (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="710cf-102">Security Roles  (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="710cf-103">ロールは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトとデータのセキュリティを管理するために、で使用され [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="710cf-103">Roles are used in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] to manage security for [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects and data.</span></span> <span data-ttu-id="710cf-104">一般的に、ロールでは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスによって管理されるオブジェクトに定義されている特定のアクセス権や権限を持つ Microsoft Windows ユーザーおよびグループのセキュリティ識別子 (SID) が関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="710cf-104">In basic terms, a role associates the security identifiers (SIDs) of Microsoft Windows users and groups that have specific access rights and permissions defined for objects managed by an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="710cf-105">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]には次の 2 種類のロールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="710cf-105">Two types of roles are provided in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="710cf-106">サーバー ロール。管理者が [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスにアクセスできるようにするための固定ロールです。</span><span class="sxs-lookup"><span data-stu-id="710cf-106">The server role, a fixed role that provides administrator access to an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="710cf-107">データベース ロール。管理者以外のユーザーによるオブジェクトやデータへのアクセスを制御するために、管理者によって定義されるロールです。</span><span class="sxs-lookup"><span data-stu-id="710cf-107">Database roles, roles defined by administrators to control access to objects and data for non-administrator users.</span></span>  
  
 <span data-ttu-id="710cf-108">セキュリティのセキュリティ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は、ロールとアクセス許可を使用して管理されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-108">Security in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] security is managed by using roles and permissions.</span></span> <span data-ttu-id="710cf-109">ロールはユーザーのグループです。</span><span class="sxs-lookup"><span data-stu-id="710cf-109">Roles are groups of users.</span></span> <span data-ttu-id="710cf-110">ユーザー (メンバーとも呼ばれる) はロールに追加したり、ロールから削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="710cf-110">Users, also called members, can be added or removed from roles.</span></span> <span data-ttu-id="710cf-111">オブジェクトに対する権限はロールによって指定されます。ロールのすべてのメンバーは、そのロールが権限を持つオブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="710cf-111">Permissions for objects are specified by roles, and all members in a role can use the objects for which the role has permissions.</span></span> <span data-ttu-id="710cf-112">ロールのすべてのメンバーは、オブジェクトに対して等しい権限を持ちます。</span><span class="sxs-lookup"><span data-stu-id="710cf-112">All members in a role have equal permissions to the objects.</span></span> <span data-ttu-id="710cf-113">権限はオブジェクトに対して適用されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-113">Permissions are particular to objects.</span></span> <span data-ttu-id="710cf-114">各オブジェクトは、そのオブジェクトに対して許可された権限のコレクションを持ちます。複数の異なる権限セットを 1 つのオブジェクトに付与できます。</span><span class="sxs-lookup"><span data-stu-id="710cf-114">Each object has a permissions collection with the permissions granted on that object, different sets of permissions can be granted on an object.</span></span> <span data-ttu-id="710cf-115">オブジェクトの権限コレクションに含まれる各権限には、1 つのロールが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="710cf-115">Each permission, from the permissions collection of the object, has a single role assigned to it.</span></span>  
  
## <a name="role-and-role-member-objects"></a><span data-ttu-id="710cf-116">Role オブジェクトと Role Member オブジェクト</span><span class="sxs-lookup"><span data-stu-id="710cf-116">Role and Role Member Objects</span></span>  
 <span data-ttu-id="710cf-117">ロールは、ユーザー (メンバー) のコレクションを格納するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="710cf-117">A role is a containing object for a collection of users (members).</span></span> <span data-ttu-id="710cf-118">ロール定義は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のユーザーのメンバーシップを設定します。</span><span class="sxs-lookup"><span data-stu-id="710cf-118">A Role definition establishes the membership of the users in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="710cf-119">権限はロールに基づいて割り当てられます。したがって、ユーザーがオブジェクトにアクセスするためには、いずれかのロールのメンバーになる必要があります。</span><span class="sxs-lookup"><span data-stu-id="710cf-119">Because permissions are assigned by role, a user must be a member of a role before the user has access to any object.</span></span>  
  
 <span data-ttu-id="710cf-120"><xref:Microsoft.AnalysisServices.Role> オブジェクトは、Name、ID、および Members の各パラメーターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-120">A <xref:Microsoft.AnalysisServices.Role> object is composed of the parameters Name, Id, and Members.</span></span> <span data-ttu-id="710cf-121">Members は文字列のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="710cf-121">Members is a collection of strings.</span></span> <span data-ttu-id="710cf-122">各メンバーには "domain\username" という形式のユーザー名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="710cf-122">Each member contains the user name in the form of "domain\username".</span></span> <span data-ttu-id="710cf-123">Name はロールの名前を表す文字列です。</span><span class="sxs-lookup"><span data-stu-id="710cf-123">Name is a string that contains the name of the role.</span></span> <span data-ttu-id="710cf-124">ID はロールの一意な識別子を表す文字列です。</span><span class="sxs-lookup"><span data-stu-id="710cf-124">ID is a string that contains the unique identifier of the role.</span></span>  
  
### <a name="server-role"></a><span data-ttu-id="710cf-125">サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="710cf-125">Server Role</span></span>  
 <span data-ttu-id="710cf-126">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバー ロールは、Windows ユーザーおよびグループによる [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスへの管理アクセスを定義します。</span><span class="sxs-lookup"><span data-stu-id="710cf-126">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server role defines administrative access of Windows users and groups to an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="710cf-127">このロールのメンバーは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのすべての [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベースおよびオブジェクトにアクセスでき、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="710cf-127">Members of this role have access to all [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] databases and objects on an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], and can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="710cf-128">SQL Server Management Studio または [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]を使用して、データベースの作成やサーバーレベルのプロパティの設定など、サーバーレベルの管理機能を実行する。</span><span class="sxs-lookup"><span data-stu-id="710cf-128">Perform server-level administrative functions using SQL Server Management Studio or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], including creating databases and setting server-level properties.</span></span>  
  
-   <span data-ttu-id="710cf-129">分析管理オブジェクト (AMO) を使用して、プログラムで管理機能を実行する。</span><span class="sxs-lookup"><span data-stu-id="710cf-129">Perform administrative functions programmatically with Analysis Management Objects (AMO).</span></span>  
  
-   <span data-ttu-id="710cf-130">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のデータベース ロールを保守する。</span><span class="sxs-lookup"><span data-stu-id="710cf-130">Maintain [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database roles.</span></span>  
  
-   <span data-ttu-id="710cf-131">トレースを開始する (プロセス アクセス権を持つデータベース ロールによって実行可能な処理イベントを除く)。</span><span class="sxs-lookup"><span data-stu-id="710cf-131">Start traces (other than for processing events, which can be performed by a database role with Process access).</span></span>  
  
 <span data-ttu-id="710cf-132">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の各インスタンスには、そのインスタンスを管理できるユーザーを定義するサーバー ロールがあります。</span><span class="sxs-lookup"><span data-stu-id="710cf-132">Every instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] has a server role that defines which users can administer that instance.</span></span> <span data-ttu-id="710cf-133">このロールの名前と ID は Administrators で、データベース ロールとは異なり、サーバー ロールは削除できず、権限を追加または削除することもできません。</span><span class="sxs-lookup"><span data-stu-id="710cf-133">The name and ID of this role is Administrators, and unlike database roles, the server role cannot be deleted, nor can permissions be added or removed.</span></span> <span data-ttu-id="710cf-134">つまり、ユーザーは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のインスタンスのサーバー ロールに含まれているかどうかによって、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のインスタンスの管理者であるかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-134">In other words, a user either is or is not an administrator for an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], depending on whether he or she is included in the server role for that instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
### <a name="database-roles"></a><span data-ttu-id="710cf-135">データベース ロール</span><span class="sxs-lookup"><span data-stu-id="710cf-135">Database Roles</span></span>  
 <span data-ttu-id="710cf-136">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のデータベース ロールは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース内のオブジェクトおよびデータへのユーザー アクセスを定義します。</span><span class="sxs-lookup"><span data-stu-id="710cf-136">An [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database role defines user access to objects and data in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="710cf-137">データベース ロールは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース内に個別のオブジェクトとして作成され、そのロールが作成されたデータベースのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-137">A database role is created as a separate object in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database, and applies only to the database in which that role is created.</span></span> <span data-ttu-id="710cf-138">Windows ユーザーおよびグループは、管理者によってこのロールに含まれています。管理者は、このロール内の権限も定義します。</span><span class="sxs-lookup"><span data-stu-id="710cf-138">Windows users and groups are included in the role by an administrator, who also defines permissions within the role.</span></span>  
  
 <span data-ttu-id="710cf-139">ロールの権限は、メンバーがデータベース内のオブジェクトとデータだけでなく、データベース自体にアクセスして管理できるようにするものです。</span><span class="sxs-lookup"><span data-stu-id="710cf-139">The permissions of a role may allow members to access and administer the database, in addition to the objects and data within the database.</span></span> <span data-ttu-id="710cf-140">各権限には 1 つまたは複数のアクセス権が関連付けられており、アクセス権によってデータベース内の特定のオブジェクトへのアクセスをさらに詳細に制御できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="710cf-140">Each permission has one or more access rights associated with it, which in turn give the permission finer control over access to a particular object in the database.</span></span>  
  
## <a name="permission-objects"></a><span data-ttu-id="710cf-141">Permission オブジェクト</span><span class="sxs-lookup"><span data-stu-id="710cf-141">Permission Objects</span></span>  
 <span data-ttu-id="710cf-142">権限は、各ロールについて、オブジェクト (キューブやディメンションなど) に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="710cf-142">Permissions are associated with an object (cube, dimension, others) for a particular role.</span></span> <span data-ttu-id="710cf-143">権限は、ロールのメンバーがオブジェクトに対して実行できる操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="710cf-143">Permissions specify what operations the member of that role can perform on that object.</span></span>  
  
 <span data-ttu-id="710cf-144"><xref:Microsoft.AnalysisServices.Permission> クラスは抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="710cf-144">The <xref:Microsoft.AnalysisServices.Permission> class is an abstract class.</span></span> <span data-ttu-id="710cf-145">そのため、対応するオブジェクトに権限を定義するには、派生クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="710cf-145">Therefore, you must use the derived classes to define permissions on the corresponding objects.</span></span> <span data-ttu-id="710cf-146">オブジェクトごとに権限の派生クラスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-146">For each object, a permission derived class is defined.</span></span>  
  
|<span data-ttu-id="710cf-147">Object</span><span class="sxs-lookup"><span data-stu-id="710cf-147">Object</span></span>|<span data-ttu-id="710cf-148">クラス</span><span class="sxs-lookup"><span data-stu-id="710cf-148">Class</span></span>|  
|------------|-----------|  
|<xref:Microsoft.AnalysisServices.Database>|<xref:Microsoft.AnalysisServices.DatabasePermission>|  
|<xref:Microsoft.AnalysisServices.DataSource>|<xref:Microsoft.AnalysisServices.DataSourcePermission>|  
|<xref:Microsoft.AnalysisServices.Dimension>|<xref:Microsoft.AnalysisServices.DimensionPermission>|  
|<xref:Microsoft.AnalysisServices.Cube>|<xref:Microsoft.AnalysisServices.CubePermission>|  
|<xref:Microsoft.AnalysisServices.MiningStructure>|<xref:Microsoft.AnalysisServices.MiningStructurePermission>|  
|<xref:Microsoft.AnalysisServices.MiningModel>|<xref:Microsoft.AnalysisServices.MiningModelPermission>|  
  
 <span data-ttu-id="710cf-149">権限によって使用可能となるアクションを以下の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="710cf-149">Possible actions enabled by permissions are shown in the list:</span></span>  
  
|<span data-ttu-id="710cf-150">アクション</span><span class="sxs-lookup"><span data-stu-id="710cf-150">Action</span></span>|<span data-ttu-id="710cf-151">値</span><span class="sxs-lookup"><span data-stu-id="710cf-151">Values</span></span>|<span data-ttu-id="710cf-152">説明</span><span class="sxs-lookup"><span data-stu-id="710cf-152">Explanation</span></span>|  
|------------|------------|-----------------|  
|<span data-ttu-id="710cf-153">Process</span><span class="sxs-lookup"><span data-stu-id="710cf-153">Process</span></span>|<span data-ttu-id="710cf-154">{`true`, `false`}</span><span class="sxs-lookup"><span data-stu-id="710cf-154">{`true`, `false`}</span></span><br /><br /> <span data-ttu-id="710cf-155">既定値 = `false`</span><span class="sxs-lookup"><span data-stu-id="710cf-155">Default=`false`</span></span>|<span data-ttu-id="710cf-156">`true` を指定した場合、メンバーはこのオブジェクトと、このオブジェクトに含まれる任意のオブジェクトを処理できます。</span><span class="sxs-lookup"><span data-stu-id="710cf-156">If `true`, members can process the object and any object that is contained in the object.</span></span><br /><br /> <span data-ttu-id="710cf-157">Process 権限はマイニング モデルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="710cf-157">Process permissions do not apply to mining models.</span></span> <span data-ttu-id="710cf-158"><xref:Microsoft.AnalysisServices.MiningModel> 権限は常に <xref:Microsoft.AnalysisServices.MiningStructure> から継承されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-158"><xref:Microsoft.AnalysisServices.MiningModel> permissions are always inherited from <xref:Microsoft.AnalysisServices.MiningStructure>.</span></span>|  
|<span data-ttu-id="710cf-159">ReadDefinition</span><span class="sxs-lookup"><span data-stu-id="710cf-159">ReadDefinition</span></span>|<span data-ttu-id="710cf-160">{`None`, `Basic`, `Allowed`}</span><span class="sxs-lookup"><span data-stu-id="710cf-160">{`None`, `Basic`, `Allowed`}</span></span><br /><br /> <span data-ttu-id="710cf-161">既定値 = `None`</span><span class="sxs-lookup"><span data-stu-id="710cf-161">Default=`None`</span></span>|<span data-ttu-id="710cf-162">オブジェクトに関連付けられたデータ定義 (ASSL) をメンバーが読み取れるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="710cf-162">Specifies whether members can read the data definition (ASSL) associated with the object.</span></span><br /><br /> <span data-ttu-id="710cf-163">`Allowed` を指定した場合、メンバーはオブジェクトに関連付けられた ASSL を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="710cf-163">If `Allowed`, members can read the ASSL associated with the object.</span></span><br /><br /> <span data-ttu-id="710cf-164">`Basic` および `Allowed` は、オブジェクトに含まれるオブジェクトによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-164">`Basic` and `Allowed` are inherited by objects that are contained in the object.</span></span> <span data-ttu-id="710cf-165">`Allowed` は `Basic` および `None` をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="710cf-165">`Allowed` overrides `Basic` and `None`.</span></span><br /><br /> <span data-ttu-id="710cf-166">オブジェクトで DISCOVER_XML_METADATA を使用する場合、`Allowed` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="710cf-166">`Allowed` is required for DISCOVER_XML_METADATA on an object.</span></span> <span data-ttu-id="710cf-167">リンク オブジェクトとローカル キューブを作成する場合、`Basic` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="710cf-167">`Basic` is required to create linked objects and local cubes.</span></span>|  
|<span data-ttu-id="710cf-168">Read</span><span class="sxs-lookup"><span data-stu-id="710cf-168">Read</span></span>|<span data-ttu-id="710cf-169">{`None`, `Allowed`}</span><span class="sxs-lookup"><span data-stu-id="710cf-169">{`None`, `Allowed`}</span></span><br /><br /> <span data-ttu-id="710cf-170">既定値 = `None` (DimensionPermission の場合は、既定値 = `Allowed`)</span><span class="sxs-lookup"><span data-stu-id="710cf-170">Default=`None` (Except for DimensionPermission, where default=`Allowed`)</span></span>|<span data-ttu-id="710cf-171">スキーマ行セットおよびデータ コンテンツへの読み取りアクセスがメンバーにあるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="710cf-171">Specifies whether members have read access to schema rowsets and data content.</span></span><br /><br /> <span data-ttu-id="710cf-172">`Allowed` を指定した場合は、データベースへの読み取りアクセスが許可され、データベースを検出できるようになります。</span><span class="sxs-lookup"><span data-stu-id="710cf-172">`Allowed` gives read access on a database, which lets you discover a database.</span></span><br /><br /> <span data-ttu-id="710cf-173">キューブに対して `Allowed` を指定した場合は、<xref:Microsoft.AnalysisServices.CellPermission> および <xref:Microsoft.AnalysisServices.CubeDimensionPermission> による制限がない限り、スキーマ行セットおよびキューブ コンテンツへの読み取りアクセスが許可されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-173">`Allowed` on a cube gives read access in schema rowsets and access to cube content (unless constrained by <xref:Microsoft.AnalysisServices.CellPermission> and <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).</span></span><br /><br /> <span data-ttu-id="710cf-174">ディメンションに対して `Allowed` を指定した場合は、<xref:Microsoft.AnalysisServices.CubeDimensionPermission> による制限がない限り、ディメンション内のすべての属性への読み取り権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-174">`Allowed` on a dimension grants that read permission on all attributes in the dimension (unless constrained by <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).</span></span> <span data-ttu-id="710cf-175">Read (読み取り) 権限は、<xref:Microsoft.AnalysisServices.CubeDimensionPermission> の静的継承でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-175">Read permission is used for static inheritance to the <xref:Microsoft.AnalysisServices.CubeDimensionPermission> only.</span></span> <span data-ttu-id="710cf-176">ディメンションに対して `None` を指定した場合は、ディメンションが非表示になり、集計可能な属性への既定のメンバーのアクセスのみが許可されます。ディメンションに集計不能な属性が含まれる場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="710cf-176">`None` on a dimension hides the dimension and gives access to the default member only for aggregatable attributes; an error is raised if the dimension contains a non-aggregatable attribute.</span></span><br /><br /> <span data-ttu-id="710cf-177"><xref:Microsoft.AnalysisServices.MiningModelPermission> に対して `Allowed` を指定した場合は、スキーマ行セット内のオブジェクトの表示権限と、予測結合の実行権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-177">`Allowed` on a <xref:Microsoft.AnalysisServices.MiningModelPermission> grants permissions to see objects in schema rowsets and to perform predict joins.</span></span><br /><br /> <span data-ttu-id="710cf-178">**注**データベース内の任意のオブジェクトの読み取りまたは書き込みを行うには、この権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="710cf-178">**NoteAllowed** is required to read or write to any object in the database.</span></span>|  
|<span data-ttu-id="710cf-179">Write</span><span class="sxs-lookup"><span data-stu-id="710cf-179">Write</span></span>|<span data-ttu-id="710cf-180">{`None`, `Allowed`}</span><span class="sxs-lookup"><span data-stu-id="710cf-180">{`None`, `Allowed`}</span></span><br /><br /> <span data-ttu-id="710cf-181">既定値 = `None`</span><span class="sxs-lookup"><span data-stu-id="710cf-181">Default=`None`</span></span>|<span data-ttu-id="710cf-182">親オブジェクトのデータへの書き込みアクセスがメンバーにあるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="710cf-182">Specifies whether members have write access to data of the parent object.</span></span><br /><br /> <span data-ttu-id="710cf-183"><xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.Cube>、および <xref:Microsoft.AnalysisServices.MiningModel> の各サブクラスにアクセスが適用されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-183">Access applies to <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, and <xref:Microsoft.AnalysisServices.MiningModel> subclasses.</span></span> <span data-ttu-id="710cf-184">データベースの <xref:Microsoft.AnalysisServices.MiningStructure> サブクラスには適用されません。検証エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="710cf-184">It does not apply to database <xref:Microsoft.AnalysisServices.MiningStructure> subclasses, which generates a validation error.</span></span><br /><br /> <span data-ttu-id="710cf-185"><xref:Microsoft.AnalysisServices.Dimension> に対して `Allowed` を指定した場合は、ディメンション内のすべての属性への書き込み権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-185">`Allowed` on a <xref:Microsoft.AnalysisServices.Dimension> grants write permission on all attributes in the dimension.</span></span><br /><br /> <span data-ttu-id="710cf-186"><xref:Microsoft.AnalysisServices.Cube> に対して `Allowed` を指定した場合は、Type=writeback として定義された各パーティションについて、キューブのセルへの書き込み権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-186">`Allowed` on a <xref:Microsoft.AnalysisServices.Cube> grants write permission on the cells of the cube for partitions defined as Type=writeback.</span></span><br /><br /> <span data-ttu-id="710cf-187"><xref:Microsoft.AnalysisServices.MiningModel> に対して `Allowed` を指定した場合は、モデル コンテンツの変更権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-187">`Allowed` on a <xref:Microsoft.AnalysisServices.MiningModel> grants permission to modify model content.</span></span><br /><br /> <span data-ttu-id="710cf-188">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、<xref:Microsoft.AnalysisServices.MiningStructure> に対して `Allowed` を指定しても特に意味はありません。</span><span class="sxs-lookup"><span data-stu-id="710cf-188">`Allowed` on a <xref:Microsoft.AnalysisServices.MiningStructure> has no specific meaning in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="710cf-189">**注:** `Allowed`Read もに設定されていない限り、書き込みをに設定することはできません。`Allowed`</span><span class="sxs-lookup"><span data-stu-id="710cf-189">**Note:**  Write cannot be set to `Allowed` unless read is also set to `Allowed`</span></span>|  
|<span data-ttu-id="710cf-190">メモの管理 **:** データベースアクセス許可のみ</span><span class="sxs-lookup"><span data-stu-id="710cf-190">Administer **Note:**  Only in Database permissions</span></span>|<span data-ttu-id="710cf-191">{`true`, `false`}</span><span class="sxs-lookup"><span data-stu-id="710cf-191">{`true`, `false`}</span></span><br /><br /> <span data-ttu-id="710cf-192">既定値 = `false`</span><span class="sxs-lookup"><span data-stu-id="710cf-192">Default=`false`</span></span>|<span data-ttu-id="710cf-193">メンバーがデータベースを管理できるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="710cf-193">Specifies whether members can administer a database.</span></span><br /><br /> <span data-ttu-id="710cf-194">`true` を指定した場合は、データベース内のすべてのオブジェクトへのアクセスが許可されます。</span><span class="sxs-lookup"><span data-stu-id="710cf-194">`true` grants members access to all objects in a database.</span></span><br /><br /> <span data-ttu-id="710cf-195">メンバーは特定のデータベースに対してのみ管理権限を持つことができます。他のデータベースを管理することはできません。</span><span class="sxs-lookup"><span data-stu-id="710cf-195">A member can have Administer permissions for a specific database, but not for others.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="710cf-196">参照</span><span class="sxs-lookup"><span data-stu-id="710cf-196">See Also</span></span>  
 [<span data-ttu-id="710cf-197">オブジェクトと操作へのアクセスの承認 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="710cf-197">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](../authorizing-access-to-objects-and-operations-analysis-services.md)  
  
  