---
title: バイナリ ラージ オブジェクト (Blob) データ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], design and implementation
ms.assetid: 97509274-c3f8-43e5-a37c-52f1ffe0961a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a663dedf34d75a21ee8df6b97979548c04abf7ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643990"
---
# <a name="binary-large-object-blob-data-sql-server"></a><span data-ttu-id="1c8ad-102">バイナリ ラージ オブジェクト (Blob) データ (SQLServer)</span><span class="sxs-lookup"><span data-stu-id="1c8ad-102">Binary Large Object (Blob) Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1c8ad-103">には、ファイルおよびドキュメントをデータベースまたはリモート ストレージ デバイスに格納するためのソリューションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-103">provides solutions for storing files and documents in the database or on remote storage devices.</span></span>  
  
##  <a name="in-this-section"></a><a name="section"></a> <span data-ttu-id="1c8ad-104">トピックの内容</span><span class="sxs-lookup"><span data-stu-id="1c8ad-104">In This Section</span></span>  
 [<span data-ttu-id="1c8ad-105">BLOB の保存オプションの比較 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c8ad-105">Compare Options for Storing Blobs &#40;SQL Server&#41;</span></span>](compare-options-for-storing-blobs-sql-server.md)  
 <span data-ttu-id="1c8ad-106">FILESTREAM、FileTable、およびリモート BLOB ストアの利点を比較します。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-106">Compare the advantages of FILESTREAM, FileTables, and Remote Blob Store.</span></span>  
  
 [<span data-ttu-id="1c8ad-107">FILESTREAM &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c8ad-107">FILESTREAM &#40;SQL Server&#41;</span></span>](filestream-sql-server.md)  
 <span data-ttu-id="1c8ad-108">FILESTREAM を使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ベースのアプリケーションで非構造化データ (ドキュメントやイメージなど) をファイル システムに格納できます。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-108">FILESTREAM enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-based applications to store unstructured data, such as documents and images, on the file system.</span></span> <span data-ttu-id="1c8ad-109">これにより、ファイル システムの豊富なストリーミング API と高いパフォーマンスをアプリケーションで活用できるほか、非構造化データとそれに対応する構造化データの間でトランザクションの一貫性も維持されます。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-109">Applications can leverage the rich streaming APIs and performance of the file system and at the same time maintain transactional consistency between the unstructured data and corresponding structured data.</span></span>  
  
 [<span data-ttu-id="1c8ad-110">FileTables &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c8ad-110">FileTables &#40;SQL Server&#41;</span></span>](filetables-sql-server.md)  
 <span data-ttu-id="1c8ad-111">FileTable 機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納されているファイル データに対して Windows ファイル名前空間のサポートと Windows アプリケーションとの互換性を提供します。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-111">The FileTable feature brings support for the Windows file namespace and compatibility with Windows applications to the file data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1c8ad-112">FileTable により、アプリケーションは、ストレージとデータ管理コンポーネントを統合し、非構造化データおよびメタデータに対する統合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス (フルテキスト検索、セマンティック検索など) を提供できます。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-112">FileTable lets an application integrate its storage and data management components, and provides integrated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services - including full-text search and semantic search - over unstructured data and metadata.</span></span>  
  
 <span data-ttu-id="1c8ad-113">つまり、ファイルおよびドキュメントを FileTable と呼ばれる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特殊なテーブルに保存しておき、ファイル システムに格納されているかのように、Windows アプリケーションからこれらのファイルおよびドキュメントにアクセスできるということです。このとき、クライアント アプリケーションに変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-113">In other words, you can store files and documents in special tables in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] called FileTables, but access them from Windows applications as if they were stored in the file system, without making any changes to your client applications.</span></span>  
  
 [<span data-ttu-id="1c8ad-114">リモート BLOB ストア &#40;RBS&#41; &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c8ad-114">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-sql-server.md)  
 <span data-ttu-id="1c8ad-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリモート BLOB ストア (RBS) を使用すると、データベース管理者は、バイナリ ラージ オブジェクト (BLOB) を、直接サーバーに格納するのではなく、汎用的なストレージ ソリューションに格納できます。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-115">Remote BLOB store (RBS) for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lets database administrators store binary large objects (BLOBs) in commodity storage solutions instead of directly on the server.</span></span> <span data-ttu-id="1c8ad-116">これにより、容量を大幅に節約でき、コストのかかるサーバー ハードウェア リソースの浪費を回避できます。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-116">This saves a significant amount of space and avoids wasting expensive server hardware resources.</span></span> <span data-ttu-id="1c8ad-117">RBS では、アプリケーションが BLOB データにアクセスするための標準化されたモデルを定義する一連の API ライブラリが提供されます。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-117">RBS provides a set of API libraries that define a standardized model for applications to access BLOB data.</span></span> <span data-ttu-id="1c8ad-118">また、RBS には、リモート BLOB データの管理に役立つメンテナンス ツール (ガベージ コレクションなど) も用意されています。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-118">RBS also includes maintenance tools, such as garbage collection, to help manage remote BLOB data.</span></span>  
  
 <span data-ttu-id="1c8ad-119">RBS は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール メディアに含まれていますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ プログラムではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="1c8ad-119">RBS is included on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media, but is not installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span>  
  
  
