---
title: クラスターノードの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster node configuration
- cluster node configuration, Setup
ms.assetid: cc960cf3-3b55-44f3-961a-eac4ad05d3d9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d2e6bf33bce3eb08994e0bd5529394e033673827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640457"
---
# <a name="cluster-node-configuration"></a><span data-ttu-id="29e48-102">クラスター ノードの構成</span><span class="sxs-lookup"><span data-stu-id="29e48-102">Cluster Node Configuration</span></span>
  <span data-ttu-id="29e48-103">フェールオーバー クラスター インスタンスにノードを追加したりノードを削除したりするには、[クラスター ノードの構成] ページを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールまたはアップグレードするには、フェールオーバー クラスターの各ノードでセットアップ プログラムを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29e48-103">Use the Cluster Node Configuration page to add or remove nodes from a failover cluster instance.To install or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run the Setup program on each node of the failover cluster.</span></span> <span data-ttu-id="29e48-104">既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターにノードを追加するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスに追加するノードで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29e48-104">To add a node to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="29e48-105">Options</span><span class="sxs-lookup"><span data-stu-id="29e48-105">Options</span></span>  
 <span data-ttu-id="29e48-106">[ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名\*\*]-ドロップダウンリストを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変更するフェールオーバークラスターインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="29e48-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance Name** - Use the drop-down list to select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance to modify.</span></span>  
  
 <span data-ttu-id="29e48-107">**[このノードの名前]** - このフィールドには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行しているコンピューターの名前が代入されます。</span><span class="sxs-lookup"><span data-stu-id="29e48-107">**Name of this node** - This field will be populated with the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="29e48-108">このコンピューターが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスで追加または削除されるフェールオーバー クラスター ノードです。</span><span class="sxs-lookup"><span data-stu-id="29e48-108">This is the failover cluster node that will be added to or removed from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
  
