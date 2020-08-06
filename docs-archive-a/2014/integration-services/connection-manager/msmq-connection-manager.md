---
title: MSMQ 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c51866eeef281f6587bf281461e4faa2278308d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644100"
---
# <a name="msmq-connection-manager"></a><span data-ttu-id="3b1f8-102">MSMQ 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="3b1f8-102">MSMQ Connection Manager</span></span>
  <span data-ttu-id="3b1f8-103">MSMQ 接続マネージャーを使用すると、Message Queuing (MSMQ) を使用するメッセージ キューにパッケージが接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-103">An MSMQ connection manager enables a package to connect to a message queue that uses Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="3b1f8-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれるメッセージ キュー タスクでは、MSMQ 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-104">The Message Queue task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses an MSMQ connection manager.</span></span>  
  
 <span data-ttu-id="3b1f8-105">MSMQ 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に MSMQ 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの `Connections` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-105">When you add an MSMQ connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an MSMQ connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="3b1f8-106">接続マネージャーの `ConnectionManagerType` プロパティは、`MSMQ` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-106">The `ConnectionManagerType` property of the connection manager is set to `MSMQ`.</span></span>  
  
 <span data-ttu-id="3b1f8-107">MSMQ 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-107">You can configure an MSMQ connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="3b1f8-108">接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-108">Provide a connection string.</span></span>  
  
-   <span data-ttu-id="3b1f8-109">接続するメッセージ キューのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-109">Provide the path of the message queue to connect to.</span></span>  
  
 <span data-ttu-id="3b1f8-110">次の表に示すように、パスの形式はキューの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-110">The format of the path depends on the type of queue, as shown in the following table.</span></span>  
  
|<span data-ttu-id="3b1f8-111">[キューの種類]</span><span class="sxs-lookup"><span data-stu-id="3b1f8-111">Queue type</span></span>|<span data-ttu-id="3b1f8-112">パスのサンプル</span><span class="sxs-lookup"><span data-stu-id="3b1f8-112">Sample path</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="3b1f8-113">パブリック</span><span class="sxs-lookup"><span data-stu-id="3b1f8-113">Public</span></span>|<span data-ttu-id="3b1f8-114">\<computer name>\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="3b1f8-114">\<computer name>\\<queue name\></span></span>|  
|<span data-ttu-id="3b1f8-115">プライベート</span><span class="sxs-lookup"><span data-stu-id="3b1f8-115">Private</span></span>|<span data-ttu-id="3b1f8-116">\<computer name>\Private$\\<queue name\></span><span class="sxs-lookup"><span data-stu-id="3b1f8-116">\<computer name>\Private$\\<queue name\></span></span>|  
  
 <span data-ttu-id="3b1f8-117">ピリオド (.) を使用してローカル コンピューターを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-117">You can use a period (.) to represent the local computer.</span></span>  
  
## <a name="configuration-of-the-msmq-connection-manager"></a><span data-ttu-id="3b1f8-118">MSMQ 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="3b1f8-118">Configuration of the MSMQ Connection Manager</span></span>  
 <span data-ttu-id="3b1f8-119">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3b1f8-120">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [MSMQ 接続マネージャー エディター](../msmq-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-120">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [MSMQ Connection Manager Editor](../msmq-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="3b1f8-121">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3b1f8-121">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1f8-122">参照</span><span class="sxs-lookup"><span data-stu-id="3b1f8-122">See Also</span></span>  
 <span data-ttu-id="3b1f8-123">[メッセージ キュー タスク](../control-flow/message-queue-task.md) </span><span class="sxs-lookup"><span data-stu-id="3b1f8-123">[Message Queue Task](../control-flow/message-queue-task.md) </span></span>  
 [<span data-ttu-id="3b1f8-124">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="3b1f8-124">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
