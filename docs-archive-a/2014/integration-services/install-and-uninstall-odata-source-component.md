---
title: OData ソースコンポーネントのインストールとアンインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad0a86c6226f408b0495569d0a853dd7340aeca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641153"
---
# <a name="install-and-uninstall-odata-source-component"></a><span data-ttu-id="a117d-102">OData ソース コンポーネントのインストールと、アンインストール</span><span class="sxs-lookup"><span data-stu-id="a117d-102">Install and Uninstall OData Source Component</span></span>
  <span data-ttu-id="a117d-103">このトピックでは、コンピューターに OData ソース コンポーネントをインストールまたは削除する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a117d-103">This topic provides instructions for installing or removing OData Source Component on your computer.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="a117d-104">インストール</span><span class="sxs-lookup"><span data-stu-id="a117d-104">Installation</span></span>  
 <span data-ttu-id="a117d-105">OData ソース コンポーネントを使用するには、前提条件となる次のコンポーネントをコンピューターにインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a117d-105">The OData Source Component requires following prerequisite components to be installed on your computer.</span></span>  
  
-   <span data-ttu-id="a117d-106">SQL Server データ ツール (パッケージの設計用)</span><span class="sxs-lookup"><span data-stu-id="a117d-106">SQL Server Data Tools (to design packages)</span></span>  
  
-   <span data-ttu-id="a117d-107">SQL Server Integration Services (Visual Studio の外部でのパッケージ実行用)</span><span class="sxs-lookup"><span data-stu-id="a117d-107">SQL Server Integration Services (to run packages outside Visual Studio)</span></span>  
  
 <span data-ttu-id="a117d-108">OData ソースコンポーネントをインストールするには、 [SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/p/?LinkId=391999)をダウンロードし、次の MSI ファイルのいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="a117d-108">To install the OData Source Component, download [SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/p/?LinkId=391999) and run one of the following MSI files.</span></span>  
  
-   <span data-ttu-id="a117d-109">64 ビット プラットフォームでは ODataSourceForSQLServer2014-amd64.msi</span><span class="sxs-lookup"><span data-stu-id="a117d-109">ODataSourceForSQLServer2014-amd64.msi for 64bit platforms</span></span>  
  
-   <span data-ttu-id="a117d-110">32 ビット プラットフォームでは ODataSourceForSQLServer2014-x86.msi</span><span class="sxs-lookup"><span data-stu-id="a117d-110">ODataSourceForSQLServer2014-x86.msi for 32bit platforms</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a117d-111">64 ビット インストーラーは、OData ソース コンポーネントの 32 ビット版と 64 ビット版の両方をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a117d-111">The 64bit installer will install both 32bit and 64bit versions of the OData Source Component.</span></span> <span data-ttu-id="a117d-112">32 ビット インストーラーを実行する必要があるのは、32 ビット OS を使用している場合のみです。</span><span class="sxs-lookup"><span data-stu-id="a117d-112">You only need to run the 32bit installer if you are using a 32bit OS.</span></span>  
  
## <a name="uninstallation"></a><span data-ttu-id="a117d-113">アンインストール</span><span class="sxs-lookup"><span data-stu-id="a117d-113">Uninstallation</span></span>  
 <span data-ttu-id="a117d-114">OData ソースコンポーネントをアンインストールするには、[**プログラムと機能**] メニューを使用します。</span><span class="sxs-lookup"><span data-stu-id="a117d-114">The OData Source component can be uninstalled from the **Programs and Features** menu.</span></span> <span data-ttu-id="a117d-115">**MICROSOFT SQL SERVER SSIS OData ソースコンポーネント (x64)** のエントリを見つけて、[**アンインストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a117d-115">Find the **Microsoft SQL Server SSIS OData Source Component (x64)** entry and click **Uninstall**.</span></span>  
  
  
