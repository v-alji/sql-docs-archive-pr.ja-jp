---
title: サーバー グループの作成または編集
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.editgroup.f1
- sql12.swb.newgroup.f1
helpviewer_keywords:
- Registered Servers [SQL Server], server groups
- server groups [SQL Server]
- groups [SQL Server], server
ms.assetid: d4a942bd-2dd1-42db-ad0e-e9a9ae5b856d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a8fbff8e52fdc91e2ed633ade725ecbb7baa5e9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737393"
---
# <a name="create-or-edit-a-server-group-sql-server-management-studio"></a><span data-ttu-id="dbbbc-102">サーバー グループの作成または編集 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="dbbbc-102">Create or Edit a Server Group (SQL Server Management Studio)</span></span>
  <span data-ttu-id="dbbbc-103">このトピックでは、サーバー グループを作成し、サーバーをそのサーバー グループに配置して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で、登録済みサーバー内のサーバーを整理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-103">This topic describes how to organize the servers in Registered Servers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by creating server groups, and placing the servers in the server groups.</span></span> <span data-ttu-id="dbbbc-104">登録済みサーバーにはサーバー グループをいつでも作成できます。また、サーバーの登録時にサーバー グループを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-104">You can create server groups in Registered Servers at any time, or you can create server groups when you register servers.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-create-a-server-group-in-registered-servers"></a><span data-ttu-id="dbbbc-105">登録済みサーバーにサーバー グループを作成するには</span><span class="sxs-lookup"><span data-stu-id="dbbbc-105">To create a server group in Registered Servers</span></span>  
  
1.  <span data-ttu-id="dbbbc-106">[登録済みサーバー] で、[登録済みサーバー] ツール バーのサーバーの種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-106">In Registered Servers, click the server type on the Registered Servers toolbar.</span></span> <span data-ttu-id="dbbbc-107">[登録済みサーバー] が表示されていない場合は、 **[表示]** メニューの **[登録済みサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-107">If Registered Servers is not visible, click **Registered Servers** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="dbbbc-108">サーバーまたはサーバー グループを右クリックし、 **[新規作成]** をポイントし、 **[サーバー グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-108">Right-click a server or a server group, point to **New**, and then click **Server Group**.</span></span>  
  
3.  <span data-ttu-id="dbbbc-109">**[新しいサーバー グループ]** ダイアログ ボックスの **[グループ名]** ボックスに、一意のサーバー グループ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-109">In the **New Server Group** dialog box, in the **Group name** list box, type a unique name for the server group.</span></span> <span data-ttu-id="dbbbc-110">このサーバー グループ名は、登録済みサーバーのツリーの現在の場所に対して一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-110">The server group name must be unique for the current location in the Registered Servers tree.</span></span>  
  
4.  <span data-ttu-id="dbbbc-111">必要に応じて、 **[グループの説明]** ボックスに、サーバー グループを説明する表示名 (「ラテン アメリカ地区の財務サーバー」など) を入力します。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-111">In the **Group description** list box, optionally type a friendly name that describes the server group, for example, "Finance Servers for Latin America."</span></span>  
  
5.  <span data-ttu-id="dbbbc-112">**[新しいサーバー グループの場所を選択する]** ボックスで、グループの場所をクリックし、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-112">In the **Select a location for the new server group** box, click a location for the group, and then click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dbbbc-113">また、サーバーの登録時でも、 **[新しいグループ]** をクリックし、 **[新しいサーバー グループ]** ダイアログ ボックスでの操作を完了すれば、新しいサーバー グループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dbbbc-113">You can also create a new server group while you are registering a server by clicking **New Group**, and then completing the **New Group** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbbc-114">参照</span><span class="sxs-lookup"><span data-stu-id="dbbbc-114">See Also</span></span>  
 [<span data-ttu-id="dbbbc-115">サーバーの登録</span><span class="sxs-lookup"><span data-stu-id="dbbbc-115">Register Servers</span></span>](register-servers.md)  
  
  
