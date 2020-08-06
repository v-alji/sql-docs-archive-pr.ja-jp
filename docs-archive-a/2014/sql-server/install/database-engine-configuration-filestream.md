---
title: データベースエンジンの構成-Filestream |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab12b507246a3e13ac59be213813604d531d9a28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720895"
---
# <a name="database-engine-configuration---filestream"></a><span data-ttu-id="3de15-102">データベース エンジンの構成 - Filestream</span><span class="sxs-lookup"><span data-stu-id="3de15-102">Database Engine Configuration - Filestream</span></span>
  <span data-ttu-id="3de15-103">このページを使用すると、このインストールの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に対して FILESTREAM を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3de15-103">Use this page to enable FILESTREAM for this installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3de15-104">FILESTREAM は、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] `varbinary(max)` バイナリラージオブジェクト (BLOB) データをファイルシステム上のファイルとして格納することにより、と NTFS ファイルシステムを統合します。</span><span class="sxs-lookup"><span data-stu-id="3de15-104">FILESTREAM integrates the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with an NTFS file system by storing `varbinary(max)` binary large object (BLOB) data as files on the file system.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="3de15-105">ステートメントでは、FILESTREAM データの挿入、更新、クエリ、検索、およびバックアップを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3de15-105">statements can insert, update, query, search, and back up FILESTREAM data.</span></span> <span data-ttu-id="3de15-106">Win32 ファイル システム インターフェイスによるデータへのストリーミング アクセスが可能になります。</span><span class="sxs-lookup"><span data-stu-id="3de15-106">Win32 file system interfaces provide streaming access to the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3de15-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="3de15-107">UI element list</span></span>  
 <span data-ttu-id="3de15-108">**[Transact-SQL アクセスに対して FILESTREAM を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="3de15-108">**Enable FILESTREAM for Transact-SQL access**</span></span>  
 <span data-ttu-id="3de15-109">[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にする場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="3de15-109">Select to enable FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="3de15-110">他のコントロール オプションを使用できるようにするには、先にこのコントロールをオンにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de15-110">This control must be checked before the other control options will be available.</span></span>  
  
 <span data-ttu-id="3de15-111">**[ファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="3de15-111">**Enable FILESTREAM for file I/O streaming access**</span></span>  
 <span data-ttu-id="3de15-112">FILESTREAM の Win32 ストリーム アクセスを有効にする場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="3de15-112">Select to enable Win32 streaming access for FILESTREAM.</span></span>  
  
 <span data-ttu-id="3de15-113">**[Windows 共有名]**</span><span class="sxs-lookup"><span data-stu-id="3de15-113">**Windows share name**</span></span>  
 <span data-ttu-id="3de15-114">このコントロールは、FILESTREAM データを格納する Windows 共有の名前を入力する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="3de15-114">Use this control to enter the name of the Windows share in which the FILESTREAM data will be stored.</span></span>  
  
 <span data-ttu-id="3de15-115">**[リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]**</span><span class="sxs-lookup"><span data-stu-id="3de15-115">**Allow remote clients to have streaming access to FILESTREAM data**</span></span>  
 <span data-ttu-id="3de15-116">このコントロールは、リモート クライアントにこのサーバー上のこの FILESTREAM データへのアクセスを許可する場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="3de15-116">Select this control to allow remote clients to access this FILESTREAM data on this server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de15-117">参照</span><span class="sxs-lookup"><span data-stu-id="3de15-117">See Also</span></span>  
 <span data-ttu-id="3de15-118">[FILESTREAM の有効化と構成](../../relational-databases/blob/enable-and-configure-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="3de15-118">[Enable and Configure FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md) </span></span>  
 [<span data-ttu-id="3de15-119">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3de15-119">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
