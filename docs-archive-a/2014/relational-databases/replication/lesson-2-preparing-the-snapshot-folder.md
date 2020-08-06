---
title: 'レッスン 2 : スナップショット フォルダーの準備 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d98c7433d0bd50504f20f7f576fcf0b20154c81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739709"
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a><span data-ttu-id="3cb46-102">レッスン 2 : スナップショット フォルダーの準備</span><span class="sxs-lookup"><span data-stu-id="3cb46-102">Lesson 2: Preparing the Snapshot Folder</span></span>
  <span data-ttu-id="3cb46-103">このレッスンでは、パブリケーション スナップショットの作成と保存に使用されるスナップショット フォルダーを設定する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="3cb46-103">In this lesson, you will learn to configure the snapshot folder that is used to create and store the publication snapshot.</span></span>  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a><span data-ttu-id="3cb46-104">スナップショット フォルダーの共有を作成し、アクセス許可を与えるには</span><span class="sxs-lookup"><span data-stu-id="3cb46-104">To create a share for the snapshot folder and assign permissions</span></span>  
  
1.  <span data-ttu-id="3cb46-105">Windows エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3cb46-105">In Windows Explorer, navigate to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data folder.</span></span> <span data-ttu-id="3cb46-106">既定の場所は、C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data です。</span><span class="sxs-lookup"><span data-stu-id="3cb46-106">The default location is C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="3cb46-107">**repldata**という名前の新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3cb46-107">Create a new folder named **repldata**.</span></span>  
  
3.  <span data-ttu-id="3cb46-108">このフォルダーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cb46-108">Right-click this folder and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="3cb46-109">**[repldata のプロパティ]** ダイアログ ボックスの **[共有]** タブで、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cb46-109">On the **Sharing** tab in the **repldata Properties** dialog box, click **Share**.</span></span>  
  
5.  <span data-ttu-id="3cb46-110">**[ファイルの共有]** ダイアログ ボックスで、 **[共有]**、 **[完了]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cb46-110">In the **File Sharing** dialog box, click **Share**, and then click **Done**.</span></span>  
  
6.  <span data-ttu-id="3cb46-111">**[セキュリティ]** タブで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cb46-111">On the **Security** tab, click **Edit**.</span></span>  
  
7.  <span data-ttu-id="3cb46-112">**[アクセス許可]** ダイアログ ボックスで **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cb46-112">In the **Permissions** dialog box, click **Add.**</span></span> <span data-ttu-id="3cb46-113">**[ユーザー、コンピューター、サービスアカウントまたはグループの選択**] ボックスに、レッスン1で作成したスナップショットエージェントアカウントの名前を _ \ repl_snapshot として入力し \<_Machine_Name> ます。ここで、**\repl_snapshot** \<*Machine_Name> \* はパブリッシャーの名前です。</span><span class="sxs-lookup"><span data-stu-id="3cb46-113">In the **Select User, Computers, Service Account, or Groups** text box, type the name of the Snapshot Agent account created in Lesson 1, as \<_Machine_Name>_**\repl_snapshot**, where \<*Machine_Name>\* is the name of the Publisher.</span></span> <span data-ttu-id="3cb46-114">[**名前の確認**]、[**OK**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cb46-114">Click **Check Names**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="3cb46-115">前の手順を繰り返して、ディストリビューションエージェントのアクセス許可、 \<_Machine_Name> _ **\ repl_distribution**、およびマージエージェント \<_Machine_Name> _を**\ repl_merge**として追加します。</span><span class="sxs-lookup"><span data-stu-id="3cb46-115">Repeat the previous step to add permissions for the Distribution Agent, as \<_Machine_Name>_**\repl_distribution**, and for the Merge Agent as \<_Machine_Name>_**\repl_merge**.</span></span>  
  
9. <span data-ttu-id="3cb46-116">次のアクセス許可が与えられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3cb46-116">Verify the following permissions are allowed:</span></span>  
  
    -   <span data-ttu-id="3cb46-117">repl_snapshot - フル コントロール</span><span class="sxs-lookup"><span data-stu-id="3cb46-117">repl_snapshot - Full Control</span></span>  
  
    -   <span data-ttu-id="3cb46-118">repl_distribution - 読み取り</span><span class="sxs-lookup"><span data-stu-id="3cb46-118">repl_distribution - Read</span></span>  
  
    -   <span data-ttu-id="3cb46-119">repl_merge - 読み取り</span><span class="sxs-lookup"><span data-stu-id="3cb46-119">repl_merge - Read</span></span>  
  
10. <span data-ttu-id="3cb46-120">**[OK]** をクリックして **[repldata のプロパティ]** ダイアログ ボックスを閉じると、repldata 共有フォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3cb46-120">Click **OK** to close the **repldata Properties** dialog box and create the repldata share.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3cb46-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="3cb46-121">Next Steps</span></span>  
 <span data-ttu-id="3cb46-122">ここでは、スナップショット フォルダーの共有を構成しました。</span><span class="sxs-lookup"><span data-stu-id="3cb46-122">You have successfully configured the share for the snapshot folder.</span></span> <span data-ttu-id="3cb46-123">次は、ディストリビューションを構成します。</span><span class="sxs-lookup"><span data-stu-id="3cb46-123">Next, you will configure distribution.</span></span> <span data-ttu-id="3cb46-124">「 [レッスン 3: ディストリビューションの構成](lesson-3-configuring-distribution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cb46-124">See [Lesson 3: Configuring Distribution](lesson-3-configuring-distribution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb46-125">参照</span><span class="sxs-lookup"><span data-stu-id="3cb46-125">See Also</span></span>  
 [<span data-ttu-id="3cb46-126">スナップショット フォルダーのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3cb46-126">Secure the Snapshot Folder</span></span>](security/secure-the-snapshot-folder.md)  
  
  
