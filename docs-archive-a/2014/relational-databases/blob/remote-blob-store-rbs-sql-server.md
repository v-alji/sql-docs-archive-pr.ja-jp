---
title: リモート BLOB ストア (RBS) [SQL Server] | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Remote Blob Store (RBS) [SQL Server]
- RBS (Remote Blob Store) [SQL Server]
ms.assetid: 31c947cf-53e9-4ff4-939b-4c1d034ea5b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f3425474ec3b9013355536424ffcf55d9426b9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712049"
---
# <a name="remote-blob-store-rbs-sql-server"></a><span data-ttu-id="70c3c-102">リモート BLOB ストア (RBS) [SQL Server]</span><span class="sxs-lookup"><span data-stu-id="70c3c-102">Remote Blob Store (RBS) (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="70c3c-103">のリモート BLOB ストア (RBS) はオプションのアドオン コンポーネントです。これを使用すると、データベース管理者は、バイナリ ラージ オブジェクトを、主なデータベース サーバーに直接格納するのではなく、汎用的なストレージ ソリューションに格納できます。</span><span class="sxs-lookup"><span data-stu-id="70c3c-103">Remote BLOB Store (RBS) is an optional add-on component that lets database administrators store binary large objects in commodity storage solutions instead of directly on the main database server.</span></span>  
  
 <span data-ttu-id="70c3c-104">RBS は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール メディアに含まれていますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ プログラムではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="70c3c-104">RBS is included on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media, but is not installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span>  
  
 <span data-ttu-id="70c3c-105">RBS の詳細については、このトピックの「 [RBS リソース](#rbsresources) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70c3c-105">For more information about RBS, see [RBS Resources](#rbsresources) in this topic.</span></span>  
  
## <a name="benefits-of-rbs"></a><span data-ttu-id="70c3c-106">RBS の利点</span><span class="sxs-lookup"><span data-stu-id="70c3c-106">Benefits of RBS</span></span>  
 <span data-ttu-id="70c3c-107">RBS には、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="70c3c-107">RBS provides the following benefits:</span></span>  
  
### <a name="optimized-database-storage-and-performance"></a><span data-ttu-id="70c3c-108">最適化されたデータベース ストレージとパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="70c3c-108">Optimized database storage and performance</span></span>  
 <span data-ttu-id="70c3c-109">BLOB をデータベースに格納する場合は、大量のファイル領域と高コストのサーバー リソースが消費されることがあります。</span><span class="sxs-lookup"><span data-stu-id="70c3c-109">Storing BLOBs in the database can consume large amounts of file space and expensive server resources.</span></span> <span data-ttu-id="70c3c-110">RBS は、BLOB を選択した専用ストレージ ソリューションに効率的に転送し、データベースにその参照を格納します。</span><span class="sxs-lookup"><span data-stu-id="70c3c-110">RBS efficiently transfers the BLOBs to a dedicated storage solution of your choosing, and stores references to them in the database.</span></span> <span data-ttu-id="70c3c-111">これにより、構造化データ用のサーバー ストレージが解放され、データベース操作用のサーバー リソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="70c3c-111">This frees server storage for structured data, and frees server resources for database operations.</span></span>  
  
### <a name="efficient-management-of-blobs"></a><span data-ttu-id="70c3c-112">BLOB の効率的な管理</span><span class="sxs-lookup"><span data-stu-id="70c3c-112">Efficient management of BLOBs</span></span>  
 <span data-ttu-id="70c3c-113">複数の RBS 機能では、格納された BLOB を容易に管理できます。</span><span class="sxs-lookup"><span data-stu-id="70c3c-113">Several RBS features support the convenient management of stored BLOBs:</span></span>  
  
-   <span data-ttu-id="70c3c-114">BLOB は、ACID (原子性、一貫性、分離性、持続性) を備えたトランザクションで管理します。</span><span class="sxs-lookup"><span data-stu-id="70c3c-114">BLOBS are managed with ACID (atomic consistency isolation durable) transactions.</span></span>  
  
-   <span data-ttu-id="70c3c-115">BLOB は、いくつかのコレクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-115">BLOBs are organized into collections.</span></span>  
  
-   <span data-ttu-id="70c3c-116">ガベージ コレクション、一貫性チェック、およびその他のメンテナンス機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-116">Garbage collection, consistency checking, and other maintenance functions are included.</span></span>  
  
### <a name="standardized-api"></a><span data-ttu-id="70c3c-117">標準化された API</span><span class="sxs-lookup"><span data-stu-id="70c3c-117">Standardized API</span></span>  
 <span data-ttu-id="70c3c-118">RBS では、アプリケーションから BLOB ストアにアクセスして変更するための標準化されたプログラミング モデルを提供する一連の API が定義されています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-118">RBS defines a set of APIs that provide a standardized programming model for applications to access and modify any BLOB store.</span></span> <span data-ttu-id="70c3c-119">各 BLOB ストアでは、独自のプロバイダー ライブラリを指定できます。このライブラリは、RBS クライアント ライブラリに接続して、BLOB の格納方法やアクセス方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="70c3c-119">Each BLOB store can specify its own provider library, which plugs into the RBS client library and specifies how BLOBs are stored and accessed.</span></span>  
  
 <span data-ttu-id="70c3c-120">多数のサード パーティのストレージ ソリューション ベンダーが、これらの標準 API に準拠し、さまざまなストレージ プラットフォームで BLOB ストレージをサポートする RBS プロバイダーを開発しています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-120">A number of third-party storage solution vendors have developed RBS providers that conform to these standard APIs and support BLOB storage on various storage platforms.</span></span>  
  
## <a name="rbs-requirements"></a><span data-ttu-id="70c3c-121">RBS 要件</span><span class="sxs-lookup"><span data-stu-id="70c3c-121">RBS Requirements</span></span>  
 <span data-ttu-id="70c3c-122">RBS では、BLOB メタデータが格納されている主なデータベース サーバー用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise が必要です。</span><span class="sxs-lookup"><span data-stu-id="70c3c-122">RBS requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise for the main database server in which the BLOB metadata is stored.</span></span> <span data-ttu-id="70c3c-123">ただし、指定された FILESTREAM プロバイダーを使用する場合は、BLOB 自体を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard に格納できます。</span><span class="sxs-lookup"><span data-stu-id="70c3c-123">However, if you use the supplied FILESTREAM provider, you can store the BLOBs themselves on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard.</span></span>  
  
 <span data-ttu-id="70c3c-124">RBS には、RBS を使用して BLOB を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスで格納できる FILESTREAM プロバイダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-124">RBS includes a FILESTREAM provider that lets you use RBS to store BLOBs on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="70c3c-125">RBS を使用して BLOB を別のストレージ ソリューションに格納する場合は、そのストレージ ソリューション用に開発されたサード パーティの RBS プロバイダーを使用するか、RBS API を使用してカスタム RBS プロバイダーを開発する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70c3c-125">If you want use RBS to store BLOBs in a different storage solution, you have to use a third party RBS provider developed for that storage solution, or develop a custom RBS provider using the RBS API.</span></span> <span data-ttu-id="70c3c-126">[Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190)には、NTFS ファイル システムに BLOB を格納するサンプル プロバイダーが学習用リソースとして用意されています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-126">A sample provider that stores BLOBs in the NTFS file system is available as a learning resource on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190).</span></span>  
  
## <a name="rbs-security"></a><span data-ttu-id="70c3c-127">RBS セキュリティ</span><span class="sxs-lookup"><span data-stu-id="70c3c-127">RBS Security</span></span>  
 <span data-ttu-id="70c3c-128">カスタム プロバイダーを使用して BLOB を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の外部に格納する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ システムをバイパスするその他のプロセスで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="70c3c-128">When you use a custom provider to store BLOBs outside of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], they may be available to other processes that bypass the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security system.</span></span> <span data-ttu-id="70c3c-129">カスタム プロバイダーが使用するストレージ メディアに適した権限と暗号化オプションで格納された BLOB が保護されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="70c3c-129">Make sure that you protect the stored BLOBs with permissions and encryption options that are appropriate to the storage medium used by the custom provider.</span></span>  
  
##  <a name="rbs-resources"></a><a name="rbsresources"></a><span data-ttu-id="70c3c-130">RBS リソース</span><span class="sxs-lookup"><span data-stu-id="70c3c-130">RBS Resources</span></span>  
 <span data-ttu-id="70c3c-131">**RBS ドキュメント**</span><span class="sxs-lookup"><span data-stu-id="70c3c-131">**RBS documentation**</span></span>  
 <span data-ttu-id="70c3c-132">RBS ドキュメントは Windows インストーラー パッケージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-132">The RBS documentation is included in the Windows installer package.</span></span> <span data-ttu-id="70c3c-133">RBS をインストールせずに RBS ドキュメントを確認する場合は、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版のドキュメントを [MSDN ライブラリからオンライン](https://go.microsoft.com/fwlink/?LinkId=210192)で参照できます。</span><span class="sxs-lookup"><span data-stu-id="70c3c-133">If you want to review the RBS documentation without installing RBS, you can view the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of the documentation [online in the MSDN Library](https://go.microsoft.com/fwlink/?LinkId=210192).</span></span>  
  
 <span data-ttu-id="70c3c-134">**RBS ホワイト ペーパー**</span><span class="sxs-lookup"><span data-stu-id="70c3c-134">**RBS white paper**</span></span>  
 <span data-ttu-id="70c3c-135">Microsoft Word 文書としてダウンロードできるホワイト ペーパー「[リモート BLOB ストレージ](https://go.microsoft.com/fwlink/?LinkId=210422)」には、RBS のインストールと構成の詳細が記載されています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-135">The white paper "[Remote BLOB Storage](https://go.microsoft.com/fwlink/?LinkId=210422)", which is available for download as a Microsoft Word document, provides detailed information about installing and configuring RBS.</span></span>  
  
 <span data-ttu-id="70c3c-136">**RBS サンプル**</span><span class="sxs-lookup"><span data-stu-id="70c3c-136">**RBS samples**</span></span>  
 <span data-ttu-id="70c3c-137">[Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190) で入手できる RBS サンプルでは、RBS アプリケーションの開発方法とカスタム RBS プロバイダーの開発およびインストール方法を示します。</span><span class="sxs-lookup"><span data-stu-id="70c3c-137">The RBS samples available on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190) demonstrate how to develop an RBS application, and how to develop and install a custom RBS provider.</span></span>  
  
 <span data-ttu-id="70c3c-138">**RBS ブログ**</span><span class="sxs-lookup"><span data-stu-id="70c3c-138">**RBS blog**</span></span>  
 <span data-ttu-id="70c3c-139">[RBS ブログ](https://go.microsoft.com/fwlink/?LinkId=210315) には、RBS の理解、配置、および維持に役立つ追加情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="70c3c-139">The [RBS blog](https://go.microsoft.com/fwlink/?LinkId=210315) provides additional information to help you understand, deploy, and maintain RBS.</span></span>  
  
  
