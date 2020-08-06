---
title: MSMQ 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41d4231ce121d596c8d818485eccf5ddf6127470
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632566"
---
# <a name="msmq-connection-manager-editor"></a><span data-ttu-id="35ff4-102">MSMQ 接続マネージャー エディター</span><span class="sxs-lookup"><span data-stu-id="35ff4-102">MSMQ Connection Manager Editor</span></span>
  <span data-ttu-id="35ff4-103">**[MSMQ 接続マネージャー]** ダイアログ ボックスでは、Message Queuing (MSMQ) メッセージ キューへのパスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="35ff4-103">Use the **MSMQ Connection Manager** dialog box to specify the path to a Message Queuing (also known as MSMQ) message queue.</span></span>  
  
 <span data-ttu-id="35ff4-104">MSMQ 接続マネージャーの詳細については、「 [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35ff4-104">To learn more about the MSMQ connection manager, see [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35ff4-105">MSMQ 接続マネージャーでは、ローカルのパブリック キューと専用キュー、およびリモートのパブリック キューがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="35ff4-105">The MSMQ connection manager supports local public and private queues and remote public queues.</span></span> <span data-ttu-id="35ff4-106">リモートの専用キューはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35ff4-106">It does not support remote private queues.</span></span> <span data-ttu-id="35ff4-107">スクリプト タスクを使用する回避策については、「 [スクリプト タスクによるリモート プライベート メッセージ キューへの送信](control-flow/script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35ff4-107">For a workaround that uses the Script Task, see [Sending to a Remote Private Message Queue with the Script Task](control-flow/script-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="35ff4-108">オプション</span><span class="sxs-lookup"><span data-stu-id="35ff4-108">Options</span></span>  
 <span data-ttu-id="35ff4-109">**Name**</span><span class="sxs-lookup"><span data-stu-id="35ff4-109">**Name**</span></span>  
 <span data-ttu-id="35ff4-110">ワークフローにおける MSMQ 接続マネージャーの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="35ff4-110">Provide a unique name for the MSMQ connection manager in the workflow.</span></span> <span data-ttu-id="35ff4-111">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="35ff4-111">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="35ff4-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="35ff4-112">**Description**</span></span>  
 <span data-ttu-id="35ff4-113">接続マネージャーの説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="35ff4-113">Describe the connection manager.</span></span> <span data-ttu-id="35ff4-114">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続マネージャーの目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35ff4-114">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="35ff4-115">**[パス]**</span><span class="sxs-lookup"><span data-stu-id="35ff4-115">**Path**</span></span>  
 <span data-ttu-id="35ff4-116">メッセージ キューの完全なパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="35ff4-116">Type the complete path of the message queue.</span></span> <span data-ttu-id="35ff4-117">パスの形式はキューの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="35ff4-117">The format of the path depends on the type of queue.</span></span>  
  
|<span data-ttu-id="35ff4-118">[キューの種類]</span><span class="sxs-lookup"><span data-stu-id="35ff4-118">Queue type</span></span>|<span data-ttu-id="35ff4-119">パスのサンプル</span><span class="sxs-lookup"><span data-stu-id="35ff4-119">Sample path</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="35ff4-120">パブリック</span><span class="sxs-lookup"><span data-stu-id="35ff4-120">Public</span></span>|<span data-ttu-id="35ff4-121">\<computer name>\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="35ff4-121">\<computer name>\\<queue name\></span></span>|  
|<span data-ttu-id="35ff4-122">プライベート</span><span class="sxs-lookup"><span data-stu-id="35ff4-122">Private</span></span>|<span data-ttu-id="35ff4-123">\<computer name>\Private$\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="35ff4-123">\<computer name>\Private$\\<queue name\></span></span>|  
  
 <span data-ttu-id="35ff4-124">"." を使用してローカル コンピューターを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="35ff4-124">You can use "." to represent the local computer.</span></span>  
  
 <span data-ttu-id="35ff4-125">**テスト**</span><span class="sxs-lookup"><span data-stu-id="35ff4-125">**Test**</span></span>  
 <span data-ttu-id="35ff4-126">MSMQ 接続マネージャーを構成した後に、 **[テスト]** をクリックして、接続が利用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="35ff4-126">After configuring the MSMQ connection manager, confirm that the connection is viable by clicking **Test**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ff4-127">参照</span><span class="sxs-lookup"><span data-stu-id="35ff4-127">See Also</span></span>  
 [<span data-ttu-id="35ff4-128">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="35ff4-128">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
