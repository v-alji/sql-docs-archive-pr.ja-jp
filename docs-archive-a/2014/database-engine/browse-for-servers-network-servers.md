---
title: '[サーバーの参照] ([ネットワーク サーバー]) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0ba5e4e5dd6d9a6541a98e0cb30229d7335bac24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642335"
---
# <a name="browse-for-servers-network-servers"></a><span data-ttu-id="d61ab-102">[サーバーの参照] ([ネットワーク サーバー])</span><span class="sxs-lookup"><span data-stu-id="d61ab-102">Browse for Servers (Network Servers)</span></span>
  <span data-ttu-id="d61ab-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントに接続する際に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの正確な名前がわからない場合は、**[サーバー名]** ボックスで **[参照]** をクリックして **[サーバーの参照]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="d61ab-103">If you are connecting to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] component and you do not know the exact name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance, click **Browse for more** in the **Server name** box to open the **Browse for Servers** dialog box.</span></span>  
  
 <span data-ttu-id="d61ab-104">サーバー コンピューターの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser サービスによって、このダイアログ ボックスの内容が自動入力されます。</span><span class="sxs-lookup"><span data-stu-id="d61ab-104">This dialog is populated by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser service on the server computers.</span></span> <span data-ttu-id="d61ab-105">インスタンス名が一覧に表示されない場合は、次のような原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="d61ab-105">There are several reasons why the name of an instance might not appear in the list:</span></span>  
  
-   <span data-ttu-id="d61ab-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行しているコンピューターで、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Browser サービスが実行されていない。</span><span class="sxs-lookup"><span data-stu-id="d61ab-106">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser service might not be running on the computer running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d61ab-107">ファイアウォールにより、UDP ポート 1434 がブロックされている。</span><span class="sxs-lookup"><span data-stu-id="d61ab-107">UDP port 1434 might be blocked by a firewall.</span></span>  
  
-   <span data-ttu-id="d61ab-108">**HideInstance** フラグが設定されている。</span><span class="sxs-lookup"><span data-stu-id="d61ab-108">The **HideInstance** flag might be set.</span></span>  
  
 <span data-ttu-id="d61ab-109">一覧に表示されないインスタンスに接続するには、TCP/IP ポート番号または名前付きパイプのパイプ名を含む、そのインスタンスの完全な接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="d61ab-109">To connect to an instance that does not appear in the list, type a full connection string for the instance, including the TCP/IP port number or the named pipes pipe name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d61ab-110">Options</span><span class="sxs-lookup"><span data-stu-id="d61ab-110">Options</span></span>  
 <span data-ttu-id="d61ab-111">**[接続に使用する、ネットワーク内の SQL Server インスタンスを選択します]**</span><span class="sxs-lookup"><span data-stu-id="d61ab-111">**Select a SQL Server instance in the network for your connection**</span></span>  
 <span data-ttu-id="d61ab-112">ツリーに表示された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスをクリックして、接続するサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="d61ab-112">Designate the server you want to connect to by clicking on the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance displayed in the tree.</span></span> <span data-ttu-id="d61ab-113">または記号でマークされたノードをクリックして、ツリービューの一部を表示または非表示にすることができ **+** **-** ます。</span><span class="sxs-lookup"><span data-stu-id="d61ab-113">You can show or hide portions of the tree view by clicking on the nodes marked with a **+** or **-** symbol.</span></span>  
  
  
