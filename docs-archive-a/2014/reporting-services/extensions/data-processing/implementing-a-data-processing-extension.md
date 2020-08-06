---
title: データ処理拡張機能の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5a1b7668f2319e742dcf3f1969fc3c5cc85cd7eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741590"
---
# <a name="implementing-a-data-processing-extension"></a><span data-ttu-id="590c7-102">データ処理拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="590c7-102">Implementing a Data Processing Extension</span></span>
  <span data-ttu-id="590c7-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能を使用することによって、データ ソースに接続し、データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="590c7-103">Data processing extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enable you to connect to a data source and retrieve data.</span></span> <span data-ttu-id="590c7-104">データ処理拡張機能は、データ ソースとデータセット間のブリッジとしても機能します。</span><span class="sxs-lookup"><span data-stu-id="590c7-104">They also serve as a bridge between a data source and a dataset.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="590c7-105">のデータ処理拡張機能は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] データ プロバイダー インターフェイスのサブセットに倣っています。</span><span class="sxs-lookup"><span data-stu-id="590c7-105">data processing extensions are modeled after a subset of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="590c7-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="590c7-106">In This Section</span></span>  
 [<span data-ttu-id="590c7-107">データ処理拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="590c7-107">Data Processing Extensions Overview</span></span>](data-processing-extensions-overview.md)  
 <span data-ttu-id="590c7-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム データ処理拡張機能の記述方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-108">Introduces how to write a custom data processing extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="590c7-109">データ処理拡張機能を実装する準備</span><span class="sxs-lookup"><span data-stu-id="590c7-109">Preparing to Implement a Data Processing Extension</span></span>](preparing-to-implement-a-data-processing-extension.md)  
 <span data-ttu-id="590c7-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を実装する場合と特定のインターフェイスを実装する必要がある場合に使用できるインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-110">Describes the interfaces available when implementing an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, as well as when you are required to implement a particular interface.</span></span>  
  
 [<span data-ttu-id="590c7-111">データ処理拡張機能ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="590c7-111">Creating a Data Processing Extension Library</span></span>](creating-a-data-processing-extension-library.md)  
 <span data-ttu-id="590c7-112">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能の名前空間の割り当て、およびライブラリ DLL へのデータ処理拡張機能のコンパイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-112">Describes assigning a namespace for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension and compiling your data processing extension into a library DLL.</span></span>  
  
 [<span data-ttu-id="590c7-113">データ処理拡張機能の Connection クラスの実装</span><span class="sxs-lookup"><span data-stu-id="590c7-113">Implementing a Connection Class for a Data Processing Extension</span></span>](implementing-a-connection-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="590c7-114">接続の属性、およびデータ処理拡張機能の独自の **Connection** クラスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-114">Describes the attributes of a connection and how to implement your own **Connection** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="590c7-115">データ処理拡張機能の Command クラスの実装</span><span class="sxs-lookup"><span data-stu-id="590c7-115">Implementing a Command Class for a Data Processing Extension</span></span>](implementing-a-command-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="590c7-116">コマンドの属性と、データ処理拡張機能の独自の **Command** クラスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-116">Describes the attributes of a command, and how to implement your own **Command** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="590c7-117">データ処理拡張機能の DataReader クラスの実装</span><span class="sxs-lookup"><span data-stu-id="590c7-117">Implementing a DataReader Class for a Data Processing Extension</span></span>](implementing-a-datareader-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="590c7-118">データ リーダーの属性と、データ処理拡張機能の独自の **DataReader** クラスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-118">Describes the attributes of a data reader and how to implement your own **DataReader** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="590c7-119">Reporting Services での外部データセットの使用</span><span class="sxs-lookup"><span data-stu-id="590c7-119">Using an External Dataset with Reporting Services</span></span>](using-an-external-dataset-with-reporting-services.md)  
 <span data-ttu-id="590c7-120">カスタム **DataSet** オブジェクトをレポート サーバーで使用するために公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-120">Describes how to expose your custom **DataSet** objects to the report server for consumption.</span></span>  
  
 [<span data-ttu-id="590c7-121">データ処理拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="590c7-121">Deploying a Data Processing Extension</span></span>](deploying-a-data-processing-extension.md)  
 <span data-ttu-id="590c7-122">データ処理拡張機能を展開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-122">Describes how to deploy your data processing extension.</span></span>  
  
 [<span data-ttu-id="590c7-123">データ処理拡張機能コードのデバッグ</span><span class="sxs-lookup"><span data-stu-id="590c7-123">Debugging Data Processing Extension Code</span></span>](debugging-data-processing-extension-code.md)  
 <span data-ttu-id="590c7-124">データ処理拡張機能のコードをデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-124">Describes how to debug code in your data processing extensions.</span></span>  
  
 [<span data-ttu-id="590c7-125">データ処理拡張機能の削除</span><span class="sxs-lookup"><span data-stu-id="590c7-125">Removing a Data Processing Extension</span></span>](removing-a-data-processing-extension.md)  
 <span data-ttu-id="590c7-126">レポート サーバーまたはレポート デザイナーからデータ処理拡張機能を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="590c7-126">Describes how to remove a data processing extension from a report server or Report Designer.</span></span>  
  
 <span data-ttu-id="590c7-127">完全に実装されたデータ処理拡張機能の例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="590c7-127">For a sample of a fully implemented data processing extension, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590c7-128">参照</span><span class="sxs-lookup"><span data-stu-id="590c7-128">See Also</span></span>  
 <span data-ttu-id="590c7-129">[Reporting Services 拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="590c7-129">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="590c7-130">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="590c7-130">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
