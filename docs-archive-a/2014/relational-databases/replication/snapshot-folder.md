---
title: '[スナップショット フォルダー] | Microsoft Docs'
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48b490c65662edf65018e98dd1bc3339f6aae6b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645499"
---
# <a name="snapshot-folder"></a><span data-ttu-id="2e4f5-102">[スナップショット フォルダー]</span><span class="sxs-lookup"><span data-stu-id="2e4f5-102">Snapshot Folder</span></span>
  <span data-ttu-id="2e4f5-103">ディストリビューションの構成ウィザードとパブリケーションの新規作成ウィザードには、 **[スナップショット フォルダー]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-103">The **Snapshot Folder** page appears in the Configure Distribution Wizard and in the New Publication Wizard.</span></span> <span data-ttu-id="2e4f5-104">このウィザードで有効にしたすべてのパブリッシャーでは、このページで指定したスナップショット フォルダーの場所が既定で使用されます (後から **[ディストリビューターのプロパティ]** ダイアログ ボックスを使用して有効にしたパブリッシャーには、この既定のスナップショット フォルダーが適用されません)。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-104">The location you specify for the snapshot folder will be used as the default for all Publishers enabled in this wizard (the default snapshot folder does not apply to Publishers that are later enabled using the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="2e4f5-105">ディストリビューションの構成ウィザードまたは **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページで、この既定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-105">You can override this default for any Publisher on the **Publishers** page of the Configure Distribution Wizard or the **Distributor Properties** dialog box.</span></span>  
  
 <span data-ttu-id="2e4f5-106">スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-106">The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it.</span></span> <span data-ttu-id="2e4f5-107">フォルダーの適切なセキュリティ保護の詳細については、「[Secure the Snapshot Folder](security/secure-the-snapshot-folder.md)」(スナップショット フォルダーのセキュリティ保護) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-107">For more information about securing the folder appropriately, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span> <span data-ttu-id="2e4f5-108">レプリケーションを実装する前に、レプリケーション エージェントがスナップショット フォルダーに接続できることをテストします。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-108">Prior to implementing replication, test that the replication agents will be able to connect to the snapshot folder.</span></span> <span data-ttu-id="2e4f5-109">各エージェントで使用されるアカウントを使用してログオンした後、スナップショット フォルダーへのアクセスを試行します。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-109">Log on under the account that will be used by each agent and then attempt to access the snapshot folder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2e4f5-110">Options</span><span class="sxs-lookup"><span data-stu-id="2e4f5-110">Options</span></span>  
 <span data-ttu-id="2e4f5-111">**[スナップショット フォルダー]**</span><span class="sxs-lookup"><span data-stu-id="2e4f5-111">**Snapshot folder**</span></span>  
 <span data-ttu-id="2e4f5-112">スナップショット ファイルを保存するフォルダーのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-112">Enter the path for the folder where you want snapshot files stored.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="2e4f5-113">はスナップショット フォルダーの場所に、ネットワーク共有を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-113">recommends that you use a network share as a snapshot folder location.</span></span> <span data-ttu-id="2e4f5-114">ローカル パス (C:\\ など、ドライブ文字で始まるパス) を使用した場合、他のコンピューター上のエージェントがアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="2e4f5-114">Local paths (those starting with a drive letter, such as C:\\) are not accessible to agents on other computers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e4f5-115">参照</span><span class="sxs-lookup"><span data-stu-id="2e4f5-115">See Also</span></span>  
 <span data-ttu-id="2e4f5-116">[代替スナップショットフォルダーの場所](alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="2e4f5-116">[Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="2e4f5-117">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="2e4f5-117">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="2e4f5-118">[パブリッシングとディストリビューションの構成](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="2e4f5-118">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="2e4f5-119">[View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="2e4f5-119">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="2e4f5-120">スナップショットを使用したサブスクリプションの初期化</span><span class="sxs-lookup"><span data-stu-id="2e4f5-120">Initialize a Subscription with a Snapshot</span></span>](initialize-a-subscription-with-a-snapshot.md)  
  
  
