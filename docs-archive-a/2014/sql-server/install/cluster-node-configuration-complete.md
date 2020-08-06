---
title: クラスターノードの構成 (完了) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64174d54-edee-49b8-9b43-039574bf2ca1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cc1f8ce4574580746e20c478b23e40485c3e6ecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640464"
---
# <a name="cluster-node-configuration-complete"></a><span data-ttu-id="069d7-102">クラスター ノードの構成 (完了)</span><span class="sxs-lookup"><span data-stu-id="069d7-102">Cluster Node Configuration (Complete)</span></span>
  <span data-ttu-id="069d7-103">[クラスター ノードの構成] (完了) ページを使用して、クラスター化用に準備されている既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールまたはアップグレードするには、フェールオーバー クラスターの各ノードでセットアップ プログラムを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="069d7-103">Use the Cluster Node Configuration (Complete) page to specify an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that has been prepared for clustering.To install or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run the Setup program on each node of the failover cluster.</span></span> <span data-ttu-id="069d7-104">既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターにノードを追加するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスに追加するノードで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="069d7-104">To add a node to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="069d7-105">Options</span><span class="sxs-lookup"><span data-stu-id="069d7-105">Options</span></span>  
 <span data-ttu-id="069d7-106">ドロップダウン ボックスから、次の項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="069d7-106">From the drop-down boxes:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="069d7-107">[インスタンス名]-フェールオーバークラスターのインスタンス名を選択し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="069d7-107">instance name - Select the instance name for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
-   <span data-ttu-id="069d7-108">このノードの名前-このフィールドには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアッププログラムが実行されているコンピューターの名前があらかじめ設定されています。</span><span class="sxs-lookup"><span data-stu-id="069d7-108">Name of this node - This field is pre-populated with the computer name where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="069d7-109">フェールオーバークラスターのネットワーク名-このフィールドには値が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="069d7-109">Failover Cluster Network Name - This field is not pre-populated.</span></span> <span data-ttu-id="069d7-110">新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスのネットワーク名を指定します。</span><span class="sxs-lookup"><span data-stu-id="069d7-110">Specify the network name for the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span> <span data-ttu-id="069d7-111">これは、ネットワーク上のフェールオーバー クラスター インスタンスを識別する名前です。</span><span class="sxs-lookup"><span data-stu-id="069d7-111">This is the name that identifies the failover cluster instance on the network.</span></span>  
  
  
