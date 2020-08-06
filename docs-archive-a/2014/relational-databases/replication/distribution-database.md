---
title: ディストリビューション データベース | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d98a80be52ae77cbdaf1581a5b3397f9d11af4fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632380"
---
# <a name="distribution-database"></a><span data-ttu-id="b6b19-102">ディストリビューション データベース</span><span class="sxs-lookup"><span data-stu-id="b6b19-102">Distribution Database</span></span>
  <span data-ttu-id="b6b19-103">ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションのトランザクションが格納されます。</span><span class="sxs-lookup"><span data-stu-id="b6b19-103">The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.</span></span>  
  
 <span data-ttu-id="b6b19-104">多くの場合、ディストリビューション データベースは 1 つで十分です。</span><span class="sxs-lookup"><span data-stu-id="b6b19-104">In many cases, a single distribution database is sufficient.</span></span> <span data-ttu-id="b6b19-105">ただし、複数のパブリッシャーが 1 つのディストリビューターを使用する場合は、各パブリッシャーにディストリビューション データベースを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b6b19-105">However, if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher.</span></span> <span data-ttu-id="b6b19-106">これによって、各ディストリビューション データベースを経由するデータ フローが区別されます。</span><span class="sxs-lookup"><span data-stu-id="b6b19-106">Doing so ensures that the data flowing through each distribution database is distinct.</span></span> <span data-ttu-id="b6b19-107">ディストリビューターに 1 つのディストリビューション データベースを指定するには、ディストリビューション構成ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6b19-107">You can specify one distribution database for the Distributor using the Configure Distribution Wizard.</span></span> <span data-ttu-id="b6b19-108">必要に応じて、 **[ディストリビューターのプロパティ]** ダイアログ ボックスで追加のディストリビューション データベースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b6b19-108">If necessary, specify additional distribution databases in the **Distributor Properties** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b6b19-109">Options</span><span class="sxs-lookup"><span data-stu-id="b6b19-109">Options</span></span>  
 <span data-ttu-id="b6b19-110">**[ディストリビューション データベース名]**</span><span class="sxs-lookup"><span data-stu-id="b6b19-110">**Distribution database name**</span></span>  
 <span data-ttu-id="b6b19-111">ディストリビューション データベースに付ける名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b6b19-111">Enter a name for the distribution database.</span></span> <span data-ttu-id="b6b19-112">ディストリビューション データベースの既定の名前は "distribution" です。</span><span class="sxs-lookup"><span data-stu-id="b6b19-112">The default name for the distribution database is 'distribution'.</span></span> <span data-ttu-id="b6b19-113">名前を付ける場合は、128 文字以内で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意であり、識別子のルールに準拠している名前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6b19-113">If you specify a name, the name can be a maximum of 128 characters, must be unique within an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and must conform to the rules for identifiers.</span></span> <span data-ttu-id="b6b19-114">詳細については、「[データベース識別子](../databases/database-identifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b19-114">For more information, see [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
 <span data-ttu-id="b6b19-115">**[ディストリビューション データベース ファイルのフォルダー]** と **[ディストリビューション データベース ログ ファイルのフォルダー]**</span><span class="sxs-lookup"><span data-stu-id="b6b19-115">**Folder for the distribution database file** and **Folder for the distribution database log file**</span></span>  
 <span data-ttu-id="b6b19-116">ディストリビューション データベース ファイルとログ ファイルのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="b6b19-116">Enter the path for the distribution database and log files.</span></span> <span data-ttu-id="b6b19-117">パスは、ディストリビューターにとってローカルなディスクを参照し、ローカル ドライブ名とコロン (C: など) で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6b19-117">Paths must refer to disks that are local to the Distributor and begin with a local drive letter and colon (for example, C:).</span></span> <span data-ttu-id="b6b19-118">マップされたドライブ名およびネットワーク パスは無効です。</span><span class="sxs-lookup"><span data-stu-id="b6b19-118">Mapped drive letters and network paths are not valid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6b19-119">ディストリビューション データベース ログをディストリビューション データベースとは別のディスク ドライブに置くようにすると、トランザクションの書き込みに要する時間が短縮され、レプリケーションのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="b6b19-119">You can decrease the time it takes to write transactions and improve the performance of replication by placing the distribution database log on a separate disk drive from the distribution database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b19-120">参照</span><span class="sxs-lookup"><span data-stu-id="b6b19-120">See Also</span></span>  
 <span data-ttu-id="b6b19-121">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="b6b19-121">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="b6b19-122">[パブリッシングとディストリビューションの構成](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="b6b19-122">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 [<span data-ttu-id="b6b19-123">ディストリビューターとパブリッシャーのプロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="b6b19-123">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)  
  
  
