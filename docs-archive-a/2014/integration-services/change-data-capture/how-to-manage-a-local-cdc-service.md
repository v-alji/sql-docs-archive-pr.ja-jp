---
title: ローカルの CDC Service を管理する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f9be649-cd93-40c1-bc48-0480106f207c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 437590d4b91f2fc80d5bb8a90251bf0dc7c8e18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710993"
---
# <a name="how-to-manage-a-local-cdc-service"></a><span data-ttu-id="3aad6-102">ローカルの CDC Service を管理する方法</span><span class="sxs-lookup"><span data-stu-id="3aad6-102">How to Manage a Local CDC Service</span></span>
  <span data-ttu-id="3aad6-103">この手順では、CDC Service 構成コンソールを使用して特定の CDC サービスを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3aad6-103">This procedure describes how to use the CDC Service Configuration Console to manage specific CDC services.</span></span>  
  
### <a name="to-manage-a-specific-cdc-service"></a><span data-ttu-id="3aad6-104">特定の CDC Service を管理するには</span><span class="sxs-lookup"><span data-stu-id="3aad6-104">To manage a specific CDC Service</span></span>  
  
1.  <span data-ttu-id="3aad6-105">**[スタート]** メニューの **[CDC Service Configuration for Oracle]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3aad6-105">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="3aad6-106">CDC Service 構成コンソールの左ペインで **[ローカルの CDC Service]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="3aad6-106">From the left pane in the CDC Service Configuration Console, expand **Local CDC Services**.</span></span>  
  
3.  <span data-ttu-id="3aad6-107">操作する CDC サービスを選択します。</span><span class="sxs-lookup"><span data-stu-id="3aad6-107">Select the CDC service you want to work with.</span></span>  
  
     <span data-ttu-id="3aad6-108">操作する CDC サービスを右クリックして、目的のアクションをクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3aad6-108">You can also right-click the CDC service you want to work with and select the desired action.</span></span>  
  
     <span data-ttu-id="3aad6-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="3aad6-109">**OR**</span></span>  
  
     <span data-ttu-id="3aad6-110">CDC Service 構成コンソールの左ペインで **[ローカルの CDC Service]** をクリックし、作業するサービスを CDC Service 構成コンソールの中央のセクションで選択します。</span><span class="sxs-lookup"><span data-stu-id="3aad6-110">Select **Local CDC Services** from the left pane in the CDC Service Configuration Console then select the service you want to work with from the middle section of the CDC Service Configuration Console.</span></span>  
  
     <span data-ttu-id="3aad6-111">操作する CDC サービスを右クリックして、目的のアクションをクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3aad6-111">You can also right-click the CDC service you want to work with and select the desired action.</span></span>  
  
4.  <span data-ttu-id="3aad6-112">CDC サービスの操作時には、以下のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3aad6-112">You can carry out the following tasks when working with a CDC service.</span></span>  
  
    -   <span data-ttu-id="3aad6-113">**サービスの削除**</span><span class="sxs-lookup"><span data-stu-id="3aad6-113">**Delete the service**</span></span>  
  
         <span data-ttu-id="3aad6-114">サービスを削除するには、CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3aad6-114">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Delete** to delete the service.</span></span>  
  
         <span data-ttu-id="3aad6-115">または、削除する CDC サービスを右クリックして **[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3aad6-115">You can also right-click the CDC service you want to delete and select **Delete**.</span></span>  
  
         <span data-ttu-id="3aad6-116">**注**: 実行中のサービスを削除した場合、サービスは停止されてから削除されます。</span><span class="sxs-lookup"><span data-stu-id="3aad6-116">**Note**: If the service is running when deleting the service, the service is stopped before being deleted.</span></span>  
  
         <span data-ttu-id="3aad6-117">Oracle CDC Windows Service の定義を削除するには、プログラムに、関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の MSXDBCDC データベースに対する更新アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="3aad6-117">To delete an Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="3aad6-118">**[OK]** をクリックしてサービスを削除すると、MSXDBCDC データベース内にある Oracle CDC Service 登録の削除が試みられます。</span><span class="sxs-lookup"><span data-stu-id="3aad6-118">When you click **OK** to delete the service, the program attempts to delete the Oracle CDC Service registration in the MSXDBCDC database.</span></span> <span data-ttu-id="3aad6-119">権限がないために削除できない場合、MSXDBCDC データベースに対する更新アクセスを持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを入力するためのダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3aad6-119">If it fails due to lack of permissions, a dialog box is displayed to prompt the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
         <span data-ttu-id="3aad6-120">[SQL Server への接続] ダイアログ ボックスに入力するデータについては、「 [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) 」および「 [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3aad6-120">For information about the data you must enter in the Connect to SQL Server dialog box, see [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) and [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).</span></span>  
  
    -   <span data-ttu-id="3aad6-121">**CDC Service のプロパティの編集**</span><span class="sxs-lookup"><span data-stu-id="3aad6-121">**Edit the CDC Service Properties**</span></span>  
  
         <span data-ttu-id="3aad6-122">CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3aad6-122">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Properties**.</span></span>  
  
         <span data-ttu-id="3aad6-123">または、プロパティを編集する CDC サービスを右クリックして **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3aad6-123">You can also right-click the CDC service where you want to edit the properties and select **Properties**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aad6-124">参照</span><span class="sxs-lookup"><span data-stu-id="3aad6-124">See Also</span></span>  
 [<span data-ttu-id="3aad6-125">Oracle CDC Service の管理</span><span class="sxs-lookup"><span data-stu-id="3aad6-125">Manage an Oracle CDC Service</span></span>](manage-an-oracle-cdc-service.md)  
  
  
