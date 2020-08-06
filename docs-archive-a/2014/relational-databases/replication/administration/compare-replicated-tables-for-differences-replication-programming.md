---
title: レプリケートされたテーブルを比較して相違があるかどうかを確認する (レプリケーション プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- tablediff utility
- comparing replicated tables
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d804c7d4ac9cc54fa144b7054c6032663b76c0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741902"
---
# <a name="compare-replicated-tables-for-differences-replication-programming"></a><span data-ttu-id="4f7c5-102">レプリケートされたテーブルを比較して相違があるかどうかを確認する (レプリケーション プログラミング)</span><span class="sxs-lookup"><span data-stu-id="4f7c5-102">Compare Replicated Tables for Differences (Replication Programming)</span></span>
  <span data-ttu-id="4f7c5-103">テーブルのアーティクル用にパブリッシュされたデータが、パブリッシャー側とサブスクライバー側とで異なっていると、データが収束しない可能性があります。アーティクルを検証することにより、両者に相違点が存在するかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-103">Article validation is used to determine if published data for table articles at the Publisher and Subscriber are not identical, which can indicate non-convergence.</span></span> <span data-ttu-id="4f7c5-104">詳細については、「[レプリケートされたデータの検証](../validate-data-at-the-subscriber.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-104">For more information, see [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span> <span data-ttu-id="4f7c5-105">ただし、検証によって返されるのは、一致しているかどうかという情報だけであり、両者のテーブル間の相違について、それ以上詳しい情報は提供されません。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-105">However, validation only returns pass or fail information and does not provide any information about what is different between the source and destination tables.</span></span> <span data-ttu-id="4f7c5-106">**tablediff** コマンド プロンプト ユーティリティを使用すると、2 つのテーブル間の詳細な相違点を取得できるだけでなく、サブスクリプションをパブリッシャー側のデータに収束させるための [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-106">The **tablediff** command prompt utility returns detailed difference information between two tables and can even generate a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script to bring a subscription into convergence with data at the Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f7c5-107">**tablediff** ユーティリティは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サーバーでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-107">The **tablediff** utility is only supported for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] servers.</span></span>  
  
### <a name="to-compare-replicated-tables-for-differences-using-tablediff"></a><span data-ttu-id="4f7c5-108">tablediff を使用してレプリケートされたテーブルを比較し相違点を確認するには</span><span class="sxs-lookup"><span data-stu-id="4f7c5-108">To compare replicated tables for differences using tablediff</span></span>  
  
1.  <span data-ttu-id="4f7c5-109">レプリケーション トポロジの任意のサーバーで、コマンド プロンプトから [tablediff Utility](../../../tools/tablediff-utility.md)を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-109">From the command prompt at any server in a replication topology, run the [tablediff Utility](../../../tools/tablediff-utility.md).</span></span> <span data-ttu-id="4f7c5-110">次のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-110">Specify the following parameters:</span></span>  
  
    -   <span data-ttu-id="4f7c5-111">**-sourceserver** - データが正しいとわかっている方のサーバー (通常はパブリッシャー) の名前。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-111">**-sourceserver** - name of the server on which the data is known to be correct, usually the Publisher.</span></span>  
  
    -   <span data-ttu-id="4f7c5-112">**-sourcedatabase** - 正しいデータが格納されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-112">**-sourcedatabase** - name of the database containing the correct data.</span></span>  
  
    -   <span data-ttu-id="4f7c5-113">**-sourcetable** - アーティクルの比較元テーブルの名前。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-113">**-sourcetable** - name of the source table for the article being compared.</span></span>  
  
    -   <span data-ttu-id="4f7c5-114">(省略可) **-sourceschema** - 比較元テーブルのスキーマ所有者 (既定のスキーマを使用しない場合)。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-114">(Optional) **-sourceschema** - schema owner of the source table, if not the default schema.</span></span>  
  
    -   <span data-ttu-id="4f7c5-115">(省略可) SQL Server 認証を使用してパブリッシャーに接続する場合は、 **-sourceuser** および **-sourcepassword** を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-115">(Optional) **-sourceuser** and **-sourcepassword** when using SQL Server Authentication to connect to the Publisher.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="4f7c5-116">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-116">When possible, use Windows Authentication.</span></span> <span data-ttu-id="4f7c5-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用する必要がある場合は、セキュリティ資格情報の入力を、ユーザーに対して実行時に求めるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-117">If you must use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="4f7c5-118">スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-118">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="4f7c5-119">**-destinationserver** - 比較対象のデータが格納されているサーバー (通常はサブスクライバー) の名前。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-119">**-destinationserver** - name of the server on which the data is being compared, usually a Subscriber.</span></span>  
  
    -   <span data-ttu-id="4f7c5-120">**-destinationdatabase** - 比較対象データベースの名前。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-120">**-destinationdatabase** - name of a the database being compared.</span></span>  
  
    -   <span data-ttu-id="4f7c5-121">**-destinationtable** - 比較対象テーブルの名前。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-121">**-destinationtable** - name of the table being compared.</span></span>  
  
    -   <span data-ttu-id="4f7c5-122">(省略可) **-destinationschema** - 比較対象テーブルのスキーマの所有者 (既定のスキーマを使用しない場合)。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-122">(Optional) **-destinationschema** - schema owner of the destination table, if not the default schema.</span></span>  
  
    -   <span data-ttu-id="4f7c5-123">(省略可) **認証を使用してサブスクライバーに接続する場合は、** -destinationuser **および** -destinationpassword [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-123">(Optional) **-destinationuser** and **-destinationpassword** when using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication to connect to the Subscriber.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="4f7c5-124">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-124">When possible, use Windows Authentication.</span></span> <span data-ttu-id="4f7c5-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用する必要がある場合は、セキュリティ資格情報の入力を、ユーザーに対して実行時に求めるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-125">If you must use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="4f7c5-126">スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-126">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="4f7c5-127">(省略可) 列レベルの比較を行う場合は、 **-c** を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-127">(Optional) Use **-c** to do a column-level comparison.</span></span>  
  
    -   <span data-ttu-id="4f7c5-128">(省略可) 短時間で処理が済むように行数およびスキーマのみの比較を行う場合は、 **-q** を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-128">(Optional) Use **-q** to do a fast, row count- and schema-only comparison.</span></span>  
  
    -   <span data-ttu-id="4f7c5-129">(省略可) **-o** に、結果の出力先ファイルの名前とパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-129">(Optional) Specify a file name and path for **-o** to output the results to a file.</span></span>  
  
    -   <span data-ttu-id="4f7c5-130">(省略可) 結果を挿入するサブスクリプション データベース内のテーブルを **-et**に指定します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-130">(Optional) Specify a table in the subscription database into which to insert results for **-et**.</span></span> <span data-ttu-id="4f7c5-131">テーブルが既に存在する場合は、 **-dt** を指定して、最初にテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-131">If the table already exists, specify **-dt** to first drop the table.</span></span>  
  
    -   <span data-ttu-id="4f7c5-132">(省略可) サブスクライバー側のデータをパブリッシャー側のデータと一致するように修正するための **ファイルを生成する場合は、** -f [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-132">(Optional) Use **-f** to generate a [!INCLUDE[tsql](../../../includes/tsql-md.md)] file to fix data at the Subscriber so that it matches data at the Publisher.</span></span> <span data-ttu-id="4f7c5-133">各ファイルの **ステートメントの数を指定するには、** -df [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-133">Use **-df** to specify the number of [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements in each file.</span></span>  
  
    -   <span data-ttu-id="4f7c5-134">(省略可) 操作を再試行する回数と再試行間隔を指定するには、 **-rc** および **-ri** を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-134">(Optional) Use **-rc** and **-ri** to specify the number of times to retry an operation and the retry interval.</span></span>  
  
    -   <span data-ttu-id="4f7c5-135">(省略可) 比較元テーブルと比較先テーブル間の完全なスキーマの比較を実行するには、 **-strict** を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f7c5-135">(Optional) Use **-strict** to enforce strict schema comparison between source and destination tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7c5-136">参照</span><span class="sxs-lookup"><span data-stu-id="4f7c5-136">See Also</span></span>  
 [<span data-ttu-id="4f7c5-137">サブスクライバーでのデータの検証</span><span class="sxs-lookup"><span data-stu-id="4f7c5-137">Validate Data at the Subscriber</span></span>](../validate-data-at-the-subscriber.md)  
  
  
