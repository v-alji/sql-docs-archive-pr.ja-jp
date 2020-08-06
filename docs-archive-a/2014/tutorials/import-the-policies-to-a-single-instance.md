---
title: 1つのインスタンスにポリシーをインポートする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0464bc6f4dcd6326a4b8f222cb4b3128f21561ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740608"
---
# <a name="import-the-policies-to-a-single-instance"></a><span data-ttu-id="9b902-102">単一インスタンスへのポリシーのインポート</span><span class="sxs-lookup"><span data-stu-id="9b902-102">Import the Policies to a Single Instance</span></span>
  <span data-ttu-id="9b902-103">ここでは、スケジュールするベスト プラクティス ポリシーを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の単一インスタンス上のポリシー ベースの管理にインポートします。</span><span class="sxs-lookup"><span data-stu-id="9b902-103">In this task, you will import the best practices policies that you want to schedule into Policy-Based Management on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9b902-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="9b902-104">Prerequisites</span></span>  
 <span data-ttu-id="9b902-105">この手順は、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降のバージョンを実行しているサーバー上で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b902-105">You must perform this procedure on a server that is running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span>  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a><span data-ttu-id="9b902-106">データベース エンジンのベスト プラクティス ポリシーのインポート</span><span class="sxs-lookup"><span data-stu-id="9b902-106">Import the best practices policies for the Database Engine</span></span>  
  
1.  <span data-ttu-id="9b902-107">を起動 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] し、に接続し [!INCLUDE[ssDE](../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9b902-107">Start [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and then connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9b902-108">オブジェクトエクスプローラーで、[**管理**]、[**ポリシー管理**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="9b902-108">In Object Explorer, expand **Management**, and then expand **Policy Management**.</span></span>  
  
3.  <span data-ttu-id="9b902-109">[**ポリシー**] を右クリックし、[**ポリシーのインポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b902-109">Right-click **Policies**, and then click **Import Policy**.</span></span>  
  
4.  <span data-ttu-id="9b902-110">[**インポート**] ダイアログボックスで、[**インポートするファイル**] ボックスの横にある省略記号ボタン ([**...**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b902-110">In the **Import** dialog box, next to the **Files to import** box, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="9b902-111">[**検索対象**] ボックスの一覧で、ベストプラクティスポリシーが含まれている次のフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="9b902-111">In the **Look in** list, browse to the following folder, which contains the best practices policies:</span></span>  
  
     <span data-ttu-id="9b902-112">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span><span class="sxs-lookup"><span data-stu-id="9b902-112">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9b902-113">ファイル パスは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プログラム ファイルのインストール先、32 ビットまたは 64 ビットのどちらのオペレーティング システムを実行しているか、および言語識別子によって異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="9b902-113">The file path may vary, depending on where you installed the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] program files, whether you are running a 32-bit or 64-bit operating system, and the language identifier.</span></span>  
  
6.  <span data-ttu-id="9b902-114">**[ポリシーの選択**] ダイアログボックスで、1つまたは複数のポリシーファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b902-114">In the **Select Policy** dialog box, select one or more policy files.</span></span>  
  
     <span data-ttu-id="9b902-115">隣接していない複数のファイルを選択するには、ファイルをクリックし、Ctrl キーを押しながら他のファイルをそれぞれクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b902-115">To select nonadjacent files, click one file, hold down the CTRL key, and then click each additional file.</span></span> <span data-ttu-id="9b902-116">隣接する複数のファイルを選択するには、最初のファイルをクリックし、Shift キーを押しながら最後のファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b902-116">To select adjacent files, click the first file in the sequence, hold down the SHIFT key, and then click the last file.</span></span>  
  
7.  <span data-ttu-id="9b902-117">ファイルの選択が完了したら、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b902-117">When you are finished selecting files, click **Open**.</span></span>  
  
8.  <span data-ttu-id="9b902-118">[**インポート**] ダイアログボックスで、[ポリシーの**状態**] ボックスの一覧が [**インポート時にポリシーの状態を保持**する] (既定値) に設定されていることを確認し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b902-118">In the **Import** dialog box, make sure that the **Policy state** list is set to **Preserve policy state on import** (the default), and then click **OK**.</span></span>  
  
     <span data-ttu-id="9b902-119">ポリシーは、[**ポリシー管理**] の下にある [**ポリシー** ] ノードにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="9b902-119">The policies are imported into the **Policies** node under **Policy Management**.</span></span> <span data-ttu-id="9b902-120">既定では、インポートされたポリシーは "要求時" 評価モードに設定されます。</span><span class="sxs-lookup"><span data-stu-id="9b902-120">By default, the imported policies are set to "On demand" evaluation mode.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9b902-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="9b902-121">Next Steps</span></span>  
 [<span data-ttu-id="9b902-122">ポリシーのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="9b902-122">Schedule the Policies</span></span>](../../2014/tutorials/schedule-the-policies.md)  
  
  
