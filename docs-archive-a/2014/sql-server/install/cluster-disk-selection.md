---
title: クラスターディスクの選択 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0f53d6d3f623254d2b17996be7fd5b8235dca223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640468"
---
# <a name="cluster-disk-selection"></a><span data-ttu-id="fc8d2-102">クラスター ディスクの選択</span><span class="sxs-lookup"><span data-stu-id="fc8d2-102">Cluster Disk Selection</span></span>
  <span data-ttu-id="fc8d2-103">**フェールオーバー クラスターの共有クラスター ディスク リソースを選択するには、** インストール ウィザードの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [クラスター ディスクの選択] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-103">Use the **Cluster Disk Selection** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to select the shared cluster disk resource for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span> <span data-ttu-id="fc8d2-104">クラスター ディスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データが配置される場所です。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-104">The cluster disk is where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data will be placed.</span></span>  
  
 <span data-ttu-id="fc8d2-105">共有クラスターディスクは、クラスターのインストールには必要ありません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-105">A shared cluster disk is not a requirement for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] cluster installations.</span></span> <span data-ttu-id="fc8d2-106">SMB ファイルサーバーは、フェールオーバークラスターインストールでサポートされている記憶域であり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] インストールを完了する前に [**データベースエンジンデータディレクトリ**] ページを使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-106">An SMB file server is a supported storage for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] failover cluster installations, and can be specified by using the **Database Engine - Data Directories** page before completing the installation.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fc8d2-107">Analysis Services のインストールを選択した場合は、共有クラスター ディスクを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-107">If you have selected Analysis Services to be installed, you must specify a shared cluster disk.</span></span>  
>   
>  <span data-ttu-id="fc8d2-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスで FILESTREAM を有効にする場合は、共有クラスター ディスクを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-108">If you plan to enable FILESTREAM on this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance, you must specify a shared cluster disk.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fc8d2-109">Options</span><span class="sxs-lookup"><span data-stu-id="fc8d2-109">Options</span></span>  
 <span data-ttu-id="fc8d2-110">**共有ディスク**</span><span class="sxs-lookup"><span data-stu-id="fc8d2-110">**Shared Disks**</span></span>  
 <span data-ttu-id="fc8d2-111">単一のディスクを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-111">Select a single disk from the list.</span></span> <span data-ttu-id="fc8d2-112">クラスター ディスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データが配置される場所です。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-112">The cluster disk is where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data will be placed.</span></span>  
  
 <span data-ttu-id="fc8d2-113">1 つのディスクのみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-113">Only one disk can be specified.</span></span> <span data-ttu-id="fc8d2-114">クラスター クォーラム リソースを含んでいるグループを選択すると、警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-114">If you select the group containing the cluster quorum resource, a warning will be displayed.</span></span> <span data-ttu-id="fc8d2-115">クラスター クォーラム リソースにインストールすることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-115">We recommend that you do not install to the cluster quorum resource.</span></span>  
  
 <span data-ttu-id="fc8d2-116">**[使用可能な共有ディスク]**</span><span class="sxs-lookup"><span data-stu-id="fc8d2-116">**Available Shared Disks**</span></span>  
 <span data-ttu-id="fc8d2-117">使用可能なディスクの一覧、各ディスクが共有ディスクに適しているかどうか、および各ディスク リソースの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc8d2-117">Displays a list of available disks, whether each is qualified as a shared disk, and a description of each disk resource.</span></span>  
  
  
