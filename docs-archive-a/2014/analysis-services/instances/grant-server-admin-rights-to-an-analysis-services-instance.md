---
title: サーバー管理者権限の付与 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
author: minewiskan
ms.author: owend
ms.openlocfilehash: 822227ae89f4f219a055bcc0d6d6b0a228f7964b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715870"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a><span data-ttu-id="1eebb-102">サーバーの管理権限の許可 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1eebb-102">Grant Server Administrator Permissions (Analysis Services)</span></span>
  <span data-ttu-id="1eebb-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス内のサーバー管理者ロールのメンバーは、そのインスタンスのすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトとデータに制限なくアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-103">Members of the Server administrator role within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] have unrestricted access to all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects and data in that instance.</span></span> <span data-ttu-id="1eebb-104">データベースの作成または処理、サーバーのプロパティの変更、トレースの起動など、イベントの処理を除くサーバー全体のタスクを実行するためには、ユーザーがサーバー管理者ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eebb-104">A user must be a member of the Server administrator role to perform any server-wide task, such as creating or processing a database, modifying server properties, or launching a trace (other than for processing events).</span></span>

 <span data-ttu-id="1eebb-105">ロールのメンバーシップは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がインストールされるときに設定されます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-105">Role membership is established when [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is installed.</span></span> <span data-ttu-id="1eebb-106">セットアップ プログラムを実行するユーザーは、サーバーを準備するときに自分または別のユーザーをロールに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-106">The user running the Setup program can add him or herself to the role, or add another user, when provisioning the server.</span></span> <span data-ttu-id="1eebb-107">次の手順に従うと、インストール後のタスクとしてロールのメンバーシップを変更できます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-107">You can modify role membership as a post-installation task using the following procedure.</span></span>

## <a name="modify-server-role-membership"></a><span data-ttu-id="1eebb-108">サーバー ロールのメンバーシップの変更</span><span class="sxs-lookup"><span data-stu-id="1eebb-108">Modify Server Role Membership</span></span>

1.  <span data-ttu-id="1eebb-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーでそのインスタンス名を右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1eebb-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and then right-click the instance name in Object Explorer and then click **Properties**.</span></span>

2.  <span data-ttu-id="1eebb-110">**[ページの選択]** ペインで **[セキュリティ]** をクリックし、ページの下部にある **[追加]** をクリックして、サーバー ロールに 1 つまたは複数の Windows ユーザーまたはグループを追加します。</span><span class="sxs-lookup"><span data-stu-id="1eebb-110">Click **Security** in the **Select a Page** pane, and then click **Add** at the bottom of the page to add one or more Windows users or groups to the server role.</span></span>

     <span data-ttu-id="1eebb-111">![Management studio の [ユーザーの追加] ダイアログボックス](../media/ssas-serveradminadd.png "Management Studio にユーザー ダイアログ ボックスを追加")</span><span class="sxs-lookup"><span data-stu-id="1eebb-111">![Add users dialog box in management studio](../media/ssas-serveradminadd.png "Add users dialog box in management studio")</span></span>

 <span data-ttu-id="1eebb-112">インストール時に、Analysis Services システム管理者としてのユーザー アカウントを 1 つ以上指定するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-112">At installation time, SQL Server Setup requires that you specify at least one user account as the Analysis Services system administrator.</span></span>

 <span data-ttu-id="1eebb-113">既定では、ローカルの Administrators グループのメンバーにも、Analysis Services の管理者権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-113">By default, members of the local Administrators group are also granted administrative rights in Analysis Server.</span></span> <span data-ttu-id="1eebb-114">ローカル グループには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のサーバー管理者ロールのメンバーシップが明示的に付与されているわけではありませんが、ローカル管理者はデータベースの作成、ユーザーとアクセス許可の追加、およびシステム管理者に許可されたその他のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-114">Although the local group is not explicitly granted membership in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server administrator role, local administrators can create databases, add users and permissions, and perform any other task allowed to system administrators.</span></span> <span data-ttu-id="1eebb-115">この動作は構成可能です。</span><span class="sxs-lookup"><span data-stu-id="1eebb-115">This behavior is configurable.</span></span> <span data-ttu-id="1eebb-116">これは、サーバープロパティによって決定され `BuiltinAdminsAreServerAdmins` ます。このプロパティは、既定で**true**に設定されています。</span><span class="sxs-lookup"><span data-stu-id="1eebb-116">It is determined by the `BuiltinAdminsAreServerAdmins` server property, which is set to **true** by default.</span></span> <span data-ttu-id="1eebb-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でこのプロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-117">You can change this property in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1eebb-118">詳細については、「 [Security Properties](../server-properties/security-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1eebb-118">For more information, see [Security Properties](../server-properties/security-properties.md).</span></span>

 <span data-ttu-id="1eebb-119">また、分析管理オブジェクト (AMO) を使用してもサーバー ロールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="1eebb-119">You can also manage server roles by using Analysis Management Objects (AMO).</span></span> <span data-ttu-id="1eebb-120">詳細については、「[分析管理オブジェクト (AMO) による開発](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1eebb-120">For more information, see [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>

## <a name="see-also"></a><span data-ttu-id="1eebb-121">参照</span><span class="sxs-lookup"><span data-stu-id="1eebb-121">See Also</span></span>
 <span data-ttu-id="1eebb-122">[オブジェクトと操作へのアクセスの承認 &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md) [セキュリティロール &#40;Analysis Services 多次元データ&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="1eebb-122">[Authorizing access to objects and operations &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md) [Security Roles  &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)</span></span>


