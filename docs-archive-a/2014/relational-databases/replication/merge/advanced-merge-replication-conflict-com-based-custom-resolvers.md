---
title: COM ベースのカスタム競合回避モジュール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b28795c1a7d43bcd4e8cb3f18723e05f9e76966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718020"
---
# <a name="com-based-custom-resolvers"></a><span data-ttu-id="9a8c9-102">COM-Based Custom Resolvers</span><span class="sxs-lookup"><span data-stu-id="9a8c9-102">COM-Based Custom Resolvers</span></span>
  <span data-ttu-id="9a8c9-103">カスタム競合回避モジュールを使用すると、既定の解決メカニズムより高い柔軟性が得られ、レプリケートされたデータを使用するアプリケーションに必要なビジネス ロジックを実装できます。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-103">Custom resolvers provide more flexibility than the default resolution mechanism, and they can implement business logic required by applications using the replicated data.</span></span> <span data-ttu-id="9a8c9-104">COM ベースのカスタム競合回避モジュールは、 **ICustomResolver** COM インターフェイス、メソッドとプロパティ、および競合解決専用に設計されたその他のインターフェイスとデータ型定義を実装するダイナミック リンク ライブラリ (DLL) です。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-104">A COM-based custom resolver is a dynamic-link library (DLL) that implements the **ICustomResolver** COM interface, its methods and properties, and other supporting interfaces and type definitions designed specifically for conflict resolution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a8c9-105">可能であれば、COM ベースのカスタム競合回避モジュールではなくビジネス ロジック ハンドラーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-105">It is recommended to use a business logic handler rather than a COM-based custom resolver if possible.</span></span> <span data-ttu-id="9a8c9-106">ビジネス ロジック ハンドラーの詳細については、「[Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md)」 (マージ同期中のビジネス ロジックの実行) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-106">For more information on business logic handlers, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="9a8c9-107">カスタム COM 競合回避モジュールを作成する場合は、replrec.dll に含まれているタイプ ライブラリを使用できます。このライブラリは、既定では [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-107">To build a custom COM resolver, you can use the type library that is provided in the replrec.dll; by default, this library is installed at [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
 <span data-ttu-id="9a8c9-108">カスタム COM 競合解決モジュールを記述する前に、以下のことを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-108">Before writing a custom COM resolver, you need to decide:</span></span>  
  
-   <span data-ttu-id="9a8c9-109">更新、挿入、削除など、解決する必要がある行の変更の種類、およびマージ変更のアップロード、ダウンロード、またはその両方で競合回避モジュールを呼び出すかどうか。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-109">The types of row changes you want to resolve, such as updates, inserts, and deletes, and whether the resolver should be invoked during the upload of merge changes, the download of merge changes, or both.</span></span> <span data-ttu-id="9a8c9-110">1 種類の変更、すべての変更、または各変更の組み合わせを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-110">You can specify one type of change, all changes, or any combination.</span></span> <span data-ttu-id="9a8c9-111">既定のマージ競合回避モジュールでは、カスタム競合回避モジュールで対応しなかった競合が処理されます。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-111">The default merge conflict resolver handles any conflicts not covered by a custom resolver.</span></span>  
  
-   <span data-ttu-id="9a8c9-112">競合の解決時に列レベルの追跡を使用するかどうか。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-112">Whether to use column tracking when resolving the conflict.</span></span> <span data-ttu-id="9a8c9-113">列レベルの追跡が有効になっている場合、競合が発生した列のデータに対してのみ競合のフラグが付けられ、それ以外の場合、データはマージされます。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-113">When column-level tracking is on, only data in those columns where a conflict exists are flagged as a conflict, otherwise the data is merged.</span></span> <span data-ttu-id="9a8c9-114">しかし、競合の解決方法は行レベルの追跡の場合と同じです。競合で優先されるデータによって行全体が上書きされます。ただし、データは、パブリッシャー、サブスクライバー、またはそれ以外で変更された値が混合されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-114">However, conflicts are resolved in the same way as row-level tracking: the priority winner overwrites the entire row of data (but the data can be a mix of values from the Publisher, Subscribers, or some altered values that were from neither Publisher nor Subscribers).</span></span> <span data-ttu-id="9a8c9-115">詳細については、「 [マージ レプリケーションの競合の検出および解決](advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-115">For more information, see [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
 <span data-ttu-id="9a8c9-116">COM ベースのカスタム競合回避モジュールを実装するには、「 [マージ アーティクルのカスタム競合回避モジュールの実装](../implement-a-custom-conflict-resolver-for-a-merge-article.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-116">To implement a COM-based custom conflict resolver, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
 <span data-ttu-id="9a8c9-117">カスタム競合回避モジュールは、パブリケーション全体ではなくアーティクルに対して指定されます。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-117">A custom resolver is specified for an article, not an entire publication.</span></span> <span data-ttu-id="9a8c9-118">複数のアーティクルで同じ競合回避モジュールを使用できますが、カスタム競合回避モジュールのロジックは特定のテーブル専用であるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-118">The same resolver can be used with more than one article, but the logic in custom resolvers is often specific to a particular table.</span></span> <span data-ttu-id="9a8c9-119">競合回避モジュールを作成した後に、アーティクルで使用されているテーブルが変更されると (競合解決に使用している列の名前が変更された場合など)、カスタム競合回避モジュールを変更して再コンパイルすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-119">If the table used in the article is modified after the resolver is created (for example, renaming the column name that is used in conflict resolution), the custom resolver might need to be modified and recompiled.</span></span>  
  
 <span data-ttu-id="9a8c9-120">カスタム競合回避モジュールを指定するには、「 [マージ アーティクル競合回避モジュールの指定](../publish/specify-a-merge-article-resolver.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8c9-120">To specify a custom resolver, see [Specify a Merge Article Resolver](../publish/specify-a-merge-article-resolver.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a8c9-121">参照</span><span class="sxs-lookup"><span data-stu-id="9a8c9-121">See Also</span></span>  
 <span data-ttu-id="9a8c9-122">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="9a8c9-122">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="9a8c9-123">Microsoft COM ベースの競合回避モジュール</span><span class="sxs-lookup"><span data-stu-id="9a8c9-123">Microsoft COM-Based Resolvers</span></span>](advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
