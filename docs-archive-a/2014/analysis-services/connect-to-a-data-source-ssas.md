---
title: データソースへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4fe7f7d5b31118369b8ce2a855b955e44f661dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633486"
---
# <a name="connect-to-a-data-source-ssas"></a><span data-ttu-id="b5bb0-102">[データ ソースへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b5bb0-102">Connect to a Data Source (SSAS)</span></span>
  <span data-ttu-id="b5bb0-103">**テーブルのインポート ウィザード** のこのページを使用すると、リレーショナル データベース、データ フィード、ファイルなど、さまざまなデータ ソースに対する新しいデータ ソース接続を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-103">This page of the **Table Import Wizard** enables you to create a new data source connection to a variety of data sources, such as relational databases, data feeds, and files.</span></span> <span data-ttu-id="b5bb0-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b5bb0-105">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-105">To connect to a data source, you must have the appropriate provider installed on your machine.</span></span> <span data-ttu-id="b5bb0-106">また、ワークスペースのデータベース サーバーにも適切なプロバイダーがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-106">You must also have the appropriate provider installed on the workspace database server.</span></span> <span data-ttu-id="b5bb0-107">32 ビット (x86) サーバーの場合は、32 ビット プロバイダーがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-107">For 32-bit (x86) servers, 32-bit providers must be installed.</span></span> <span data-ttu-id="b5bb0-108">64 ビット (x64) サーバーの場合は、64 ビット プロバイダーがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-108">For 64-bit (x64) servers, 64-bit providers must be installed.</span></span>  
  
 <span data-ttu-id="b5bb0-109">アーキテクチャに関係なく、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] は常に 32 ビット プロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-109">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] always runs in a 32-bit process, regardless of architecture.</span></span> <span data-ttu-id="b5bb0-110">64 ビット コンピューターで [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を実行している場合は、データ プロバイダーをインストールする際に、次の点に注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-110">When running [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] on a 64-bit machine, you should be aware of the following when installing data providers:</span></span>  
  
-   <span data-ttu-id="b5bb0-111">32 ビットと 64 ビットのサイド バイ サイド インストールをサポートするプロバイダーの場合は、両方のプロバイダーをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-111">For providers that support side-by-side installation of 32-bit and 64-bit providers, you should install both providers.</span></span>  
  
-   <span data-ttu-id="b5bb0-112">ACE プロバイダーの場合は、64 ビット バージョンのプロバイダーをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-112">For the ACE provider, you must install the 64-bit version of the provider.</span></span> <span data-ttu-id="b5bb0-113">ACE プロバイダーは Office によって自動的にインストールされるため、ワークスペース データベース サーバーをホストする 64 ビット コンピューターでは 32 ビット バージョンの Microsoft Office を実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-113">Because Office automatically installs the ACE provider, you should not run a 32-bit version of Microsoft Office on a 64-bit machine hosting the workspace database server.</span></span>  
  
     <span data-ttu-id="b5bb0-114">ACE プロバイダーは、テキスト ファイル、Excel ファイル、および Access ファイルからのインポートに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-114">The ACE provider is used to import from Text, Excel, and Access files.</span></span> <span data-ttu-id="b5bb0-115">これらのデータ ソースをサポートする必要がない場合は、64 ビットのワークスペース データベース サーバーが実行されているコンピューターで、32 ビット バージョンの Microsoft Office を実行してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-115">If support for these data sources is not needed, you can then run a 32-bit version of Microsoft Office on a machine running a 64-bit workspace database server.</span></span>  
  
-   <span data-ttu-id="b5bb0-116">32 ビットと 64 ビットのサイド バイ サイド インストールをサポートしないその他のプロバイダーについては、32 ビットのプロバイダーをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-116">For other providers that do not support side-by-side installation of 32-bit and 64-bit providers, you must install the 32-bit provider.</span></span> <span data-ttu-id="b5bb0-117">64 ビット コンピューターしか利用できない場合は、ワークスペース データベース サーバーとして 64 ビットのプロバイダーがインストールされたリモート コンピューターを使用してください。</span><span class="sxs-lookup"><span data-stu-id="b5bb0-117">If only 64-bit machines are available, you must use a remote machine with a 64-bit provider installed as the workspace database server.</span></span>  
  
  
