---
title: Analysis Services Server 上のユーザーとセッションを切断する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ending user activity [Analysis Services]
- connections [Analysis Services]
- sessions [Analysis Services]
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: bac20b663b0a65902c70e7a3c3bfe3f27b7bf061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714749"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a><span data-ttu-id="f1af6-102">Analysis Services サーバー上のユーザーとセッションの切断</span><span class="sxs-lookup"><span data-stu-id="f1af6-102">Disconnect Users and Sessions on Analysis Services Server</span></span>
  <span data-ttu-id="f1af6-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の管理者は、ワークロード管理の一環としてユーザー操作を終了できます。</span><span class="sxs-lookup"><span data-stu-id="f1af6-103">An administrator of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] may want to end user activity as part of workload management.</span></span> <span data-ttu-id="f1af6-104">ユーザー操作を終了するには、セッションと接続を取り消します。</span><span class="sxs-lookup"><span data-stu-id="f1af6-104">You do this by canceling sessions and connections.</span></span> <span data-ttu-id="f1af6-105">セッションは、クエリの実行時に自動的に作成される場合 (暗黙的) と、管理者が作成時に名前を付ける場合 (明示的) があります。</span><span class="sxs-lookup"><span data-stu-id="f1af6-105">Sessions can be formed automatically when a query is run (implicit), or named at the time of creation by the administrator (explicit).</span></span> <span data-ttu-id="f1af6-106">接続は、クエリを実行できる開かれたパイプのようなものです。</span><span class="sxs-lookup"><span data-stu-id="f1af6-106">Connections are open conduits over which queries can be run.</span></span> <span data-ttu-id="f1af6-107">セッションと接続は両方とも、アクティブなときに終了できます。</span><span class="sxs-lookup"><span data-stu-id="f1af6-107">Both sessions and connections can be ended while they are active.</span></span> <span data-ttu-id="f1af6-108">たとえば、処理に時間がかかりすぎる場合や、実行中のコマンドが正しく記述されているかどうかについて疑問が生じた場合、管理者はセッションの処理を終了できます。</span><span class="sxs-lookup"><span data-stu-id="f1af6-108">For example, an administrator may want to end processing for a session if the processing is taking too long or if some doubt has arisen as to whether the command being executed was written correctly.</span></span>  
  
## <a name="ending-sessions-and-connections"></a><span data-ttu-id="f1af6-109">セッションと接続の終了</span><span class="sxs-lookup"><span data-stu-id="f1af6-109">Ending Sessions and Connections</span></span>  
 <span data-ttu-id="f1af6-110">セッションおよび接続の管理には、動的管理ビュー (DMV) および XMLA を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1af6-110">To manage sessions and connections, you can use Dynamic Management Views (DMVs) and XMLA:</span></span>  
  
1.  <span data-ttu-id="f1af6-111">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、Analysis Services インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f1af6-111">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an Analysis Services instance.</span></span>  
  
2.  <span data-ttu-id="f1af6-112">現在実行中のすべてのセッション、接続、およびコマンドのリストを取得するには、次のいずれかの DMV クエリを MDX クエリ ウィンドウに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f1af6-112">Paste any one of the following DMV queries in an MDX query window to get a list of all sessions, connections, and commands that are currently executing:</span></span>  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  <span data-ttu-id="f1af6-113">F5 キーを押してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f1af6-113">Press F5 to execute the query.</span></span>  
  
     <span data-ttu-id="f1af6-114">DMV クエリは、セッションと接続の情報を、読み取りやコピーが容易な表形式の結果セットとして返します。</span><span class="sxs-lookup"><span data-stu-id="f1af6-114">The DMV query returns session and connection information in a tabular result set that is easier read and copy from.</span></span>  
  
 <span data-ttu-id="f1af6-115">クエリ ウィンドウを開いた状態にします。</span><span class="sxs-lookup"><span data-stu-id="f1af6-115">Keep the query window open.</span></span> <span data-ttu-id="f1af6-116">次の手順では、切断するセッションの SPID をコピーするために、このページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f1af6-116">In the next step, you will want to return to this page to copy the SPIDs of the session you want to disconnect.</span></span>  
  
 <span data-ttu-id="f1af6-117">セッションを終了するために、XMLA クエリ ウィンドウをもう 1 つ開きます。</span><span class="sxs-lookup"><span data-stu-id="f1af6-117">To end a session, open a second XMLA query window.</span></span>  
  
1.  <span data-ttu-id="f1af6-118">次の構文を MDX クエリ ウィンドウに貼り付けます。ConnectionID、SessionID、または SPID プレースホルダーは、前の手順からコピーした有効な値に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="f1af6-118">Paste the following syntax into an MDX query window, replacing the ConnectionID, SessionID, or SPID placeholder with a valid value copied from the previous step.</span></span>  
  
    ```  
    <Cancel xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  <span data-ttu-id="f1af6-119">F5 キーを押してキャンセル コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f1af6-119">Press F5 to execute the cancel command.</span></span>  
  
 <span data-ttu-id="f1af6-120">接続を終了すると、すべてのセッションと SPID が取り消され、ホスト セッションが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="f1af6-120">Ending a connection cancels all sessions and SPIDs, closing the host session.</span></span>  
  
 <span data-ttu-id="f1af6-121">セッションを終了すると、そのセッションの一部として実行されているすべてのコマンド (SPID) が停止します。</span><span class="sxs-lookup"><span data-stu-id="f1af6-121">Ending a session stops all commands (SPIDs) that are running as part of that session.</span></span>  
  
 <span data-ttu-id="f1af6-122">SPID を終了すると、特定のコマンドが取り消されます。</span><span class="sxs-lookup"><span data-stu-id="f1af6-122">Ending a SPID cancels a particular commend.</span></span>  
  
 <span data-ttu-id="f1af6-123">まれに、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で接続に関連付けられているすべてのセッションおよび SPID を追跡できない場合 (HTTP シナリオで複数のセッションが開かれている場合など) は、接続を閉じることができません。</span><span class="sxs-lookup"><span data-stu-id="f1af6-123">In rare cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will not close a connection if it cannot track all the sessions and SPIDs associated with the connection (for example, when multiple sessions are open in an HTTP scenario).</span></span>  
  
 <span data-ttu-id="f1af6-124">このトピックで参照された XMLA の詳細については、[「Execute メソッド (XMLA)」](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) および [「Cancel 要素 (XMLA)」](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1af6-124">For more information about the XMLA referenced in this topic, see [Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) and [Cancel Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1af6-125">参照</span><span class="sxs-lookup"><span data-stu-id="f1af6-125">See Also</span></span>  
 <span data-ttu-id="f1af6-126">[XMLA&#41;&#40;の接続とセッションの管理](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md) </span><span class="sxs-lookup"><span data-stu-id="f1af6-126">[Managing Connections and Sessions &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md) </span></span>  
 <span data-ttu-id="f1af6-127">[XMLA&#41;&#40;BeginSession 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="f1af6-127">[BeginSession Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla) </span></span>  
 <span data-ttu-id="f1af6-128">[XMLA&#41;&#40;EndSession 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="f1af6-128">[EndSession Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla) </span></span>  
 [<span data-ttu-id="f1af6-129">Session 要素 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="f1af6-129">Session Element &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
