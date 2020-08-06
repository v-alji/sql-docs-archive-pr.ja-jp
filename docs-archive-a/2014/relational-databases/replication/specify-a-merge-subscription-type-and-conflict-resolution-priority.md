---
title: マージサブスクリプションの種類と競合解決の優先度を指定します (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a19ae6246fe59308283fbaf2f35e2c49f96b140c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743209"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a><span data-ttu-id="8fd38-102">マージ サブスクリプションの種類と競合解決の優先度の指定 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8fd38-102">Specify a Merge Subscription Type and Conflict Resolution Priority (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8fd38-103">サブスクリプションの新規作成ウィザードの **[サブスクリプションの種類]** ページで、マージ サブスクリプションの種類と競合解決の優先度を指定します。</span><span class="sxs-lookup"><span data-stu-id="8fd38-103">Specify a merge subscription type and conflict resolution priority on the **Subscription Type** page of the New Subscription Wizard.</span></span> <span data-ttu-id="8fd38-104">このウィザードの使用方法の詳細については、「 [Create a Pull Subscription](create-a-pull-subscription.md) 」および「 [Create a Push Subscription](create-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fd38-104">For more information about using this wizard, see [Create a Pull Subscription](create-a-pull-subscription.md) and [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="8fd38-105">サブスクリプションの種類はサブスクリプションの作成後には変更できませんが、サーバー サブスクリプションの種類の優先度は、 **[サブスクリプションのプロパティ - \<Publisher>:\<PublicationDatabase>]** ダイアログ ボックスで変更できます。</span><span class="sxs-lookup"><span data-stu-id="8fd38-105">Subscription type cannot be modified after a subscription is created, but priority can be modified for the server subscription type in the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box.</span></span> <span data-ttu-id="8fd38-106">このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) 」および「 [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fd38-106">For more information about accessing this dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a><span data-ttu-id="8fd38-107">マージ サブスクリプションの種類と競合解決の優先度を指定するには</span><span class="sxs-lookup"><span data-stu-id="8fd38-107">To specify a merge subscription type and conflict resolution priority</span></span>  
  
1.  <span data-ttu-id="8fd38-108">サブスクリプションの新規作成ウィザードの **[サブスクリプションの種類]** ページで、 **[サブスクリプションの種類]** オプションに対して **[クライアント]** または **[サーバー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8fd38-108">On the **Subscription Type** page of the New Subscription Wizard, select **Client** or **Server** for the **Subscription Type** option.</span></span>  
  
2.  <span data-ttu-id="8fd38-109">サブスクリプションの種類として **[サーバー]** を選択した場合は、 **[競合解決の優先度]** オプションの値 (0.00 ～ 99.99) も入力します。</span><span class="sxs-lookup"><span data-stu-id="8fd38-109">If you select a subscription type of **Server**, also enter a value (0.00 to 99.99) for the **Priority for Conflict Resolution** option.</span></span>  
  
### <a name="to-modify-the-conflict-resolution-priority"></a><span data-ttu-id="8fd38-110">競合解決の優先度を変更するには</span><span class="sxs-lookup"><span data-stu-id="8fd38-110">To modify the conflict resolution priority</span></span>  
  
1.  <span data-ttu-id="8fd38-111">パブリッシャーの **[サブスクリプションのプロパティ - \<Publisher>:\<PublicationDatabase>]** で、 **[優先度]** オプションの値 (0.00 ～ 99.99) を入力します。</span><span class="sxs-lookup"><span data-stu-id="8fd38-111">In the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** at the Publisher, enter a value (0.00 to 99.99) for the **Priority** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8fd38-112">参照</span><span class="sxs-lookup"><span data-stu-id="8fd38-112">See Also</span></span>  
 <span data-ttu-id="8fd38-113">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="8fd38-113">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="8fd38-114">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="8fd38-114">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
