---
title: 'コマンドライン管理ツール: SqlLocalDB.exe |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d21a6a8879e981e52bd2e7d3bd05a37e65d8cf4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632485"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a><span data-ttu-id="95199-102">コマンド ライン管理ツール: SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="95199-102">Command-Line Management Tool: SqlLocalDB.exe</span></span>
  <span data-ttu-id="95199-103">SqlLocalDB.exe は、コマンド ラインから LocalDB インスタンスを簡単に管理できるシンプルなツールです。</span><span class="sxs-lookup"><span data-stu-id="95199-103">SqlLocalDB.exe is a simple tool that enables the user to easily manage LocalDB instances from the command line.</span></span> <span data-ttu-id="95199-104">LocalDB インスタンスの API の単純なラッパーとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="95199-104">It is implemented as a simple wrapper around the LocalDB instance API.</span></span> <span data-ttu-id="95199-105">SQLCMD などの多くの SQL Server ツールの場合と同様、パラメーターはコマンド ライン引数として SqlLocalDB に渡され、出力はコンソールに送られます。</span><span class="sxs-lookup"><span data-stu-id="95199-105">As in many similar SQL Server tools (for example, SQLCMD), parameters are passed to SqlLocalDB as command-line arguments and output is sent to the console.</span></span>  
  
 <span data-ttu-id="95199-106">SqlLocalDB では、開発者が LocalDB を使用できます。API を呼び出すコードを記述したり、他のツールを使用したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="95199-106">SqlLocalDB enables developers to use LocalDB without having to write code to call the API or depend on other tools to do it for them.</span></span>  
  
## <a name="sqllocaldb-options"></a><span data-ttu-id="95199-107">SqlLocalDB オプション</span><span class="sxs-lookup"><span data-stu-id="95199-107">SqlLocalDB Options</span></span>  
 <span data-ttu-id="95199-108">SqlLocalDB では、次のオプションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="95199-108">SqlLocalDB supports the following options.</span></span>  
  
|<span data-ttu-id="95199-109">オプション</span><span class="sxs-lookup"><span data-stu-id="95199-109">Option</span></span>|<span data-ttu-id="95199-110">実行内容</span><span class="sxs-lookup"><span data-stu-id="95199-110">What it does</span></span>|  
|------------|------------------|  
|`-?`|<span data-ttu-id="95199-111">ヘルプ テキストを出力します。</span><span class="sxs-lookup"><span data-stu-id="95199-111">Prints help text.</span></span>|  
|`create&#124;c "instance name" [version-number] [-s]`|<span data-ttu-id="95199-112">指定された名前とバージョンで LocalDB インスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="95199-112">Creates a new LocalDB instance with a specified name and version.</span></span><br /><br /> <span data-ttu-id="95199-113">[version-number] パラメーターを省略した場合、既定で SqlLocalDB ビルド バージョンになります。</span><span class="sxs-lookup"><span data-stu-id="95199-113">If the [version-number] parameter is omitted, it defaults to the SqlLocalDB build version.</span></span><br /><br /> <span data-ttu-id="95199-114">-s は、LocalDB インスタンスの新規作成後に、そのインスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="95199-114">-s starts the new LocalDB instance after it is created.</span></span>|  
|`delete&#124;d "instance name"`|<span data-ttu-id="95199-115">指定した名前の LocalDB インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="95199-115">Deletes the LocalDB instance with the specified name.</span></span>|  
|`start&#124;s "instance name"`|<span data-ttu-id="95199-116">指定した名前の LocalDB インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="95199-116">Starts the LocalDB instance with the specified name.</span></span>|  
|`stop&#124;p "instance name" [-i&#124;-k]`|<span data-ttu-id="95199-117">現在のクエリの実行が終了した後、指定した名前の LocalDB インスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="95199-117">Stops the LocalDB instance with the specified name, after current queries finish running.</span></span><br /><br /> <span data-ttu-id="95199-118">-i は、NOWAIT オプション付きで LocalDB インスタンスのシャットダウンを要求します。</span><span class="sxs-lookup"><span data-stu-id="95199-118">-i requests the LocalDB instance shutdown with the NOWAIT option.</span></span><br /><br /> <span data-ttu-id="95199-119">-k は、LocalDB インスタンス プロセスに通知することなく、そのプロセスを停止します。</span><span class="sxs-lookup"><span data-stu-id="95199-119">-k kills the LocalDB instance process without contacting it.</span></span>|  
|`share&#124;h ["owner SID or account"] "private name" "shared name"`|<span data-ttu-id="95199-120">指定された共有名を使用して、指定されたプライベート インスタンスを共有します。</span><span class="sxs-lookup"><span data-stu-id="95199-120">Shares the specified private instance using the specified shared name.</span></span> <span data-ttu-id="95199-121">ユーザー SID またはアカウント名を省略した場合、既定で現在のユーザーになります。</span><span class="sxs-lookup"><span data-stu-id="95199-121">If the user SID or account name is omitted, it defaults to the current user.</span></span>|  
|`unshare&#124;u "shared name"`|<span data-ttu-id="95199-122">指定された共有 LocalDB インスタンスの共有を解除します。</span><span class="sxs-lookup"><span data-stu-id="95199-122">Unshares the specified shared LocalDB instance.</span></span>|  
|`info&#124;i`|<span data-ttu-id="95199-123">現在のユーザーが所有している既存のすべての LocalDB インスタンス、および共有されているすべての LocalDB インスタンスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="95199-123">Lists all existing LocalDB instances that are owned by the current user and all shared LocalDB instances.</span></span>|  
|`info&#124;i "instance name"`|<span data-ttu-id="95199-124">指定された LocalDB インスタンスに関する情報を出力します。</span><span class="sxs-lookup"><span data-stu-id="95199-124">Prints the information about the specified LocalDB instance.</span></span>|  
|`versions&#124;v`|<span data-ttu-id="95199-125">コンピューターにインストールされているすべての LocalDB バージョンを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="95199-125">Lists all LocalDB versions installed on the computer.</span></span>|  
|||  
|`trace&#124;t on&#124;off`|<span data-ttu-id="95199-126">トレースのオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="95199-126">Turns tracing on and off.</span></span>|  
  
 <span data-ttu-id="95199-127">SqlLocalDB では、スペースを区切り文字として扱います。スペースと特殊文字が含まれるインスタンス名は、引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="95199-127">SqlLocalDB treats spaces as delimiters; you must surround the instance names that contain spaces and special characters with quotes.</span></span> <span data-ttu-id="95199-128">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="95199-128">For example:</span></span>  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
