---
title: グループを追加する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f9da1d558ccb648af8fbc0dd3b802751bd5ae44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736486"
---
# <a name="add-a-group-master-data-services"></a><span data-ttu-id="89ff1-102">グループを追加する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="89ff1-102">Add a Group (Master Data Services)</span></span>
  <span data-ttu-id="89ff1-103">**で** [グループ] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ボックスの一覧にグループを追加して、Web アプリケーションに権限を割り当てるプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="89ff1-103">Add a group to the **Groups** list in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to begin the process of assigning permission to the Web application.</span></span> <span data-ttu-id="89ff1-104">グループ内のユーザーが [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスできるようにするには、グループの権限を 1 つまたは複数の機能領域およびモデル オブジェクトに付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89ff1-104">Before a user in the group can access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you must give the group permission to one or more functional areas and model objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="89ff1-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="89ff1-105">Prerequisites</span></span>  
 <span data-ttu-id="89ff1-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="89ff1-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="89ff1-107">**[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="89ff1-107">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
### <a name="to-add-a-group"></a><span data-ttu-id="89ff1-108">グループを追加するには</span><span class="sxs-lookup"><span data-stu-id="89ff1-108">To add a group</span></span>  
  
1.  <span data-ttu-id="89ff1-109">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ff1-109">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="89ff1-110">**[ユーザー]** ページでメニュー バーから **[グループの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ff1-110">On the **Users** page, from the menu bar, click **Manage Groups**.</span></span>  
  
3.  <span data-ttu-id="89ff1-111">**[グループの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ff1-111">Click **Add groups**.</span></span>  
  
4.  <span data-ttu-id="89ff1-112">グループの名前を Active Directory ドメイン名またはサーバー コンピューターの名前の後に入力します ( *domain\group_name* または *computer\group_name*のように入力します)。</span><span class="sxs-lookup"><span data-stu-id="89ff1-112">Type the group's name preceded by the Active Directory domain name or by the server computer's name, as in *domain\group_name* or *computer\group_name*.</span></span>  
  
5.  <span data-ttu-id="89ff1-113">必要に応じて、 **[名前の確認]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ff1-113">Optionally, click **Check names**.</span></span>  
  
6.  <span data-ttu-id="89ff1-114">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89ff1-114">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89ff1-115">ユーザーが最初に [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスしたときに、そのユーザーの名前が [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザー一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="89ff1-115">When the user first accesses [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], the user's name is added to the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] list of users.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="89ff1-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="89ff1-116">Next Steps</span></span>  
  
-   [<span data-ttu-id="89ff1-117">機能領域の権限を割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="89ff1-117">Assign Functional Area Permissions &#40;Master Data Services&#41;</span></span>](assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="89ff1-118">参照</span><span class="sxs-lookup"><span data-stu-id="89ff1-118">See Also</span></span>  
 [<span data-ttu-id="89ff1-119">セキュリティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="89ff1-119">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
