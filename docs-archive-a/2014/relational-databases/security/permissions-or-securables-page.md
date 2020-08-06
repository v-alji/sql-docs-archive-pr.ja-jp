---
title: '[権限] ページまたは [セキュリティ保護可能なリソース] ページ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.permissions.f1
- sql12.swb.SecurableAndEffectPermissions.f1
- sql12.swb.availabilitygroupproperties.permission.f1
- sql12.swb.common.columnperm.f1
- sql12.swb.SecurableAndEffectivePermission.f1
ms.assetid: b3bf077a-bec2-4161-ac0c-460586199906
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 80417c720258833850f07eb67f83f5c47f487ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714030"
---
# <a name="permissions-or-securables-page"></a><span data-ttu-id="49941-102">[権限] ページまたは [セキュリティ保護可能なリソース] ページ</span><span class="sxs-lookup"><span data-stu-id="49941-102">Permissions or Securables Page</span></span>
  <span data-ttu-id="49941-103">**[権限]** ページまたは **[セキュリティ保護可能なリソース]** ページを使用すると、セキュリティ保護可能なリソースに対する権限を表示または設定できます。</span><span class="sxs-lookup"><span data-stu-id="49941-103">Use the **Permissions** page or the **Securables** page to view or set the permissions for securables.</span></span> <span data-ttu-id="49941-104">このページは、さまざまな場面で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="49941-104">This page can be opened from many locations.</span></span> <span data-ttu-id="49941-105">このページの内容は、ページを開くときの状況やページに含まれているアイテムによって多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="49941-105">The contents of the page can change slightly, depending on how the page is opened and what it contains.</span></span> <span data-ttu-id="49941-106">ページの先頭にあるグリッドは、ページを開いたときに設定されます。それ以外では、空になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="49941-106">The top grid of the page might be populated when the page opens, or it might be empty.</span></span> <span data-ttu-id="49941-107">アイテムを上のグリッドに追加するには、 **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49941-107">To add items to the upper grid, click **Search**.</span></span> <span data-ttu-id="49941-108">上のグリッドでアイテムを選択した後、 **[明示的]** タブで適切な権限を設定します。集計された権限を表示するには、 **[有効]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="49941-108">In the upper grid, select an item, and then set the appropriate permissions on the **Explicit** tab. To view aggregated permissions, use the **Effective** tab.</span></span>  
  
 <span data-ttu-id="49941-109">セキュリティ保護可能なリソースとプリンシパルの有効な組み合わせの詳細については、「[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)」に記載されている、セキュリティ保護可能なリソース別の構文に関するリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49941-109">To understand the possible combinations of securables and principals, see the securable-specific syntax links in the topic [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span> <span data-ttu-id="49941-110">詳細については、「 [セキュリティ保護可能](securables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49941-110">For more information, see [Securables](securables.md).</span></span>  
  
## <a name="page-header"></a><span data-ttu-id="49941-111">ページ ヘッダー</span><span class="sxs-lookup"><span data-stu-id="49941-111">Page Header</span></span>  
 <span data-ttu-id="49941-112">**[権限]** ページまたは **[セキュリティ保護可能なリソース]** ページのヘッダーは、セキュリティ保護可能なリソースまたはプリンシパルによって異なります。</span><span class="sxs-lookup"><span data-stu-id="49941-112">The header of the **Permissions** or **Securables** page varies depending on the securable or principal.</span></span> <span data-ttu-id="49941-113">ここには、アイテムの名前など、アイテムに関連する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49941-113">It displays information relevant to the item, such as its name.</span></span>  
  
## <a name="upper-grid"></a><span data-ttu-id="49941-114">上のグリッド</span><span class="sxs-lookup"><span data-stu-id="49941-114">Upper Grid</span></span>  
 <span data-ttu-id="49941-115">上のグリッドには、権限を設定できるアイテムが 1 つ以上表示されます。</span><span class="sxs-lookup"><span data-stu-id="49941-115">The upper grid contains one or more items for which permissions can be set.</span></span> <span data-ttu-id="49941-116">このダイアログ ボックスには、上のグリッドに追加するオブジェクトまたはプリンシパルを選択するための **[検索]** ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="49941-116">This dialog box provides the **Search** button for selecting objects or principals to add to the upper grid.</span></span> <span data-ttu-id="49941-117">グリッドの名前には、 **[セキュリティ保護可能なリソース]** 、または 1 つ以上の種類のセキュリティ保護可能なリソースやプリンシパルが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="49941-117">The name of the grid might display **Securables** or one or more types of securables or principals.</span></span> <span data-ttu-id="49941-118">上のグリッドに表示される列は、プリンシパルまたはセキュリティ保護可能なリソースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="49941-118">The columns that are displayed in the upper grid vary depending on the principal or securable.</span></span>  
  
 <span data-ttu-id="49941-119">**名前**</span><span class="sxs-lookup"><span data-stu-id="49941-119">**Name**</span></span>  
 <span data-ttu-id="49941-120">グリッドに追加される各プリンシパルまたはセキュリティ保護可能なリソースの名前です。</span><span class="sxs-lookup"><span data-stu-id="49941-120">The name of each principal or securable that is added to the grid.</span></span>  
  
 <span data-ttu-id="49941-121">**Type**</span><span class="sxs-lookup"><span data-stu-id="49941-121">**Type**</span></span>  
 <span data-ttu-id="49941-122">各アイテムの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="49941-122">Describes the type of each item.</span></span>  
  
## <a name="explicit-tab"></a><span data-ttu-id="49941-123">[明示的] タブ</span><span class="sxs-lookup"><span data-stu-id="49941-123">Explicit Tab</span></span>  
 <span data-ttu-id="49941-124">**[明示的]** タブには、上のグリッドで選択されているセキュリティ保護可能なリソースに適用できる権限が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49941-124">The **Explicit** tab lists the possible permissions for the securable that are selected in the upper grid.</span></span> <span data-ttu-id="49941-125">権限を構成するには、 **[許可]** (または **[許容]** )、 **[許可の有無]** 、または **[拒否]** チェック ボックスをオンあるいはオフにします。</span><span class="sxs-lookup"><span data-stu-id="49941-125">To configure the permissions, select or clear the **Grant** (or **Allow**), **With Grant**, and **Deny** check boxes.</span></span> <span data-ttu-id="49941-126">すべての明示的な権限に対してすべてのオプションを使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="49941-126">All options are not available for all explicit permissions.</span></span>  
  
 <span data-ttu-id="49941-127">**アクセス許可**</span><span class="sxs-lookup"><span data-stu-id="49941-127">**Permissions**</span></span>  
 <span data-ttu-id="49941-128">権限の名前です。</span><span class="sxs-lookup"><span data-stu-id="49941-128">The name of the permission.</span></span>  
  
 <span data-ttu-id="49941-129">**Grantor**</span><span class="sxs-lookup"><span data-stu-id="49941-129">**Grantor**</span></span>  
 <span data-ttu-id="49941-130">権限を許可したプリンシパルです。</span><span class="sxs-lookup"><span data-stu-id="49941-130">The principal that granted the permission.</span></span>  
  
 <span data-ttu-id="49941-131">**Grant**</span><span class="sxs-lookup"><span data-stu-id="49941-131">**Grant**</span></span>  
 <span data-ttu-id="49941-132">この権限をログインに対して許可する場合はオンにします。</span><span class="sxs-lookup"><span data-stu-id="49941-132">Select to grant this permission to the login.</span></span> <span data-ttu-id="49941-133">この権限を取り消す場合はオフにします。</span><span class="sxs-lookup"><span data-stu-id="49941-133">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="49941-134">**[許可の有無]**</span><span class="sxs-lookup"><span data-stu-id="49941-134">**With Grant**</span></span>  
 <span data-ttu-id="49941-135">一覧表示された権限に対する WITH GRANT オプションの状態を反映します。</span><span class="sxs-lookup"><span data-stu-id="49941-135">Reflects the state of the WITH GRANT option for the listed permission.</span></span> <span data-ttu-id="49941-136">このボックスは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="49941-136">This box is read-only.</span></span> <span data-ttu-id="49941-137">この権限を適用するには、 [GRANT](/sql/t-sql/statements/grant-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="49941-137">To apply this permission, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="49941-138">**Deny**</span><span class="sxs-lookup"><span data-stu-id="49941-138">**Deny**</span></span>  
 <span data-ttu-id="49941-139">この権限をログインに対して拒否する場合はオンにします。</span><span class="sxs-lookup"><span data-stu-id="49941-139">Select to deny this permission to the login.</span></span> <span data-ttu-id="49941-140">この権限を取り消す場合はオフにします。</span><span class="sxs-lookup"><span data-stu-id="49941-140">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="49941-141">**[列権限]**</span><span class="sxs-lookup"><span data-stu-id="49941-141">**Column Permissions**</span></span>  
 <span data-ttu-id="49941-142">列を含むオブジェクト (テーブル、ビュー、テーブル値関数など) の場合、 **[列権限]** ボタンをクリックすると、 **[列権限]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49941-142">For objects that contain columns (such as tables, views, or table-valued functions), the **Column Permissions** button opens the **Column Permissions** dialog box.</span></span> <span data-ttu-id="49941-143">このダイアログ ボックスでは、テーブルまたはビューの各列に対して **[許可]** 、 **[許容]** または **[拒否]** の権限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="49941-143">In this dialog box, you can set **Grant**, **Allow**, or **Deny** permissions on individual columns of a table or view.</span></span> <span data-ttu-id="49941-144">このオプションは、すべての種類のオブジェクトや権限で使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="49941-144">This option is not available for all object types or permissions.</span></span>  
  
## <a name="effective-tab"></a><span data-ttu-id="49941-145">[有効] タブ</span><span class="sxs-lookup"><span data-stu-id="49941-145">Effective Tab</span></span>  
 <span data-ttu-id="49941-146">プリンシパルがセキュリティ保護可能なリソースに関連付けた権限は、複数の異なるプリンシパルに設定されている権限から継承されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="49941-146">The permissions that a principal has related to a securable may come from permissions that are set for several different principals.</span></span> <span data-ttu-id="49941-147">たとえば、ログインは個別に権限が与えられるだけでなく、グループのメンバーとしても権限が与えられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="49941-147">For example, a login might be granted permissions individually and also as a member of a group.</span></span> <span data-ttu-id="49941-148">**[有効]** タブでは、明示的な権限と、グループまたはロールのメンバーシップから受け取る権限を組み合わせた結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49941-148">The **Effective** tab shows the result of combining explicit permissions and the permissions that are received from group or role memberships.</span></span> <span data-ttu-id="49941-149">許可の権限は集計されます。</span><span class="sxs-lookup"><span data-stu-id="49941-149">Grant permissions are aggregated.</span></span> <span data-ttu-id="49941-150">また、すべての許可の権限を拒否の権限がオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="49941-150">A deny permission overrides all grant permissions.</span></span>  
  
 <span data-ttu-id="49941-151">**アクセス許可**</span><span class="sxs-lookup"><span data-stu-id="49941-151">**Permissions**</span></span>  
 <span data-ttu-id="49941-152">権限の名前です。</span><span class="sxs-lookup"><span data-stu-id="49941-152">The name of the permission.</span></span>  
  
 <span data-ttu-id="49941-153">**列**</span><span class="sxs-lookup"><span data-stu-id="49941-153">**Column**</span></span>  
 <span data-ttu-id="49941-154">権限の影響を受ける列の名前です。</span><span class="sxs-lookup"><span data-stu-id="49941-154">The names of columns that are affected by the permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49941-155">参照</span><span class="sxs-lookup"><span data-stu-id="49941-155">See Also</span></span>  
 <span data-ttu-id="49941-156">[データベース レベルのロール](authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="49941-156">[Database-Level Roles](authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="49941-157">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="49941-157">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
