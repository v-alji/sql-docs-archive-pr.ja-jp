---
title: 通常の接続とコンテキスト接続に関する制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 52f50347a27cdaffe83b252d86c56382b5ef4f31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642129"
---
# <a name="restrictions-on-regular-and-context-connections"></a><span data-ttu-id="e8fd7-102">通常の接続とコンテキスト接続に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="e8fd7-102">Restrictions on Regular and Context Connections</span></span>
  <span data-ttu-id="e8fd7-103">このトピックでは、コンテキストと通常の接続を使用してプロセスで実行されるコードに関連する制限事項について説明し [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-103">This topic discusses the restrictions associated with code executing in the [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] process through context and regular connections.</span></span>  
  
## <a name="restrictions-on-context-connections"></a><span data-ttu-id="e8fd7-104">コンテキスト接続に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="e8fd7-104">Restrictions on Context Connections</span></span>  
 <span data-ttu-id="e8fd7-105">アプリケーションを開発するときは、コンテキスト接続に適用される次の制限事項を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-105">When developing your application, take into account the following restrictions that apply to context connections:</span></span>  
  
-   <span data-ttu-id="e8fd7-106">特定の接続に対して特定の時点に開くことができるコンテキスト接続は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-106">You can have only one context connection open at a given time for a given connection.</span></span> <span data-ttu-id="e8fd7-107">複数のステートメントをそれぞれ独立した接続で同時に実行する場合、その中の 1 つの接続しか独自のコンテキスト接続を取得できません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-107">If you have multiple statements running concurrently in separate connections, each one of them can get their own context connection.</span></span> <span data-ttu-id="e8fd7-108">この制限事項は、異なる接続からの同時実行要求には影響しません。つまり、特定の接続の特定の要求にしか影響しません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-108">The restriction does not affect concurrent requests from different connections; it only affects a given request on a given connection.</span></span>  
  
-   <span data-ttu-id="e8fd7-109">コンテキスト接続では、MARS (複数のアクティブな結果セット) がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-109">Multiple Active Result Sets (MARS) is not supported in a context connection.</span></span>  
  
-   <span data-ttu-id="e8fd7-110">コンテキスト接続では、`SqlBulkCopy` クラスを使用できません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-110">The `SqlBulkCopy` class does not operate in a context connection.</span></span>  
  
-   <span data-ttu-id="e8fd7-111">コンテキスト接続では、更新バッチ処理がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-111">Update batching in a context connection is not supported</span></span>  
  
-   <span data-ttu-id="e8fd7-112">`SqlNotificationRequest` は、コンテキスト接続に対して実行するコマンドと併用できません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-112">`SqlNotificationRequest` cannot be used with commands that execute against a context connection.</span></span>  
  
-   <span data-ttu-id="e8fd7-113">コンテキスト接続に対して実行しているコマンドはキャンセルできません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-113">Canceling commands that are running against the context connection is not supported.</span></span> <span data-ttu-id="e8fd7-114">`SqlCommand.Cancel` メソッドでは、この要求が暗黙に無視されます。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-114">The `SqlCommand.Cancel` method silently ignores the request.</span></span>  
  
-   <span data-ttu-id="e8fd7-115">"context connection=true" を使用する場合は、他の接続文字列キーワードを使用できません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-115">No other connection string keywords can be used when you use "context connection=true".</span></span>  
  
-   <span data-ttu-id="e8fd7-116">`SqlConnection.DataSource` の接続文字列が、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス名ではなく、"context connection=true" である場合、`SqlConnection` プロパティは NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-116">The `SqlConnection.DataSource` property returns null if the connection string for the `SqlConnection` is "context connection=true", instead of the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e8fd7-117">コンテキスト接続に対してコマンドを実行する場合に `SqlCommand.CommandTimeout` プロパティを設定しても、影響はありません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-117">Setting the `SqlCommand.CommandTimeout` property has no effect when the command is executed against a context connection.</span></span>  
  
## <a name="restrictions-on-regular-connections"></a><span data-ttu-id="e8fd7-118">通常の接続に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="e8fd7-118">Restrictions on Regular Connections</span></span>  
 <span data-ttu-id="e8fd7-119">アプリケーションを開発するときは、通常の接続に適用される次の制限事項を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-119">When developing your application, take into account the following restrictions that apply to regular connections:</span></span>  
  
-   <span data-ttu-id="e8fd7-120">内部サーバーに対する非同期コマンドの実行はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-120">Asynchronous command execution against internal servers is not supported.</span></span> <span data-ttu-id="e8fd7-121">コマンドの接続文字列に "async=true" を含めてコマンドを実行すると、`System.NotSupportedException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-121">Including "async=true" in the connection string of a command, and then executing the command, results in `System.NotSupportedException` being thrown.</span></span> <span data-ttu-id="e8fd7-122">このメッセージが表示されます。 "プロセス内で実行中の非同期処理はサポートされていません [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。"</span><span class="sxs-lookup"><span data-stu-id="e8fd7-122">This message appears: "Asynchronous processing is not supported when running inside the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process."</span></span>  
  
-   <span data-ttu-id="e8fd7-123">`SqlDependency` オブジェクトはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e8fd7-123">`SqlDependency` object is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8fd7-124">参照</span><span class="sxs-lookup"><span data-stu-id="e8fd7-124">See Also</span></span>  
 [<span data-ttu-id="e8fd7-125">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="e8fd7-125">Context Connection</span></span>](context-connection.md)  
  
  
