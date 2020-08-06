---
title: '[クエリオプション] の [実行] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.general.f1
ms.assetid: 858a0263-2f04-4692-b8bf-63e93c998ead
author: rothja
ms.author: jroth
ms.openlocfilehash: ce3848b51b81f111333ba0e9ac12c96432dd9863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644131"
---
# <a name="query-options-execution-general-page"></a><span data-ttu-id="fe205-102">[クエリ オプション] の [実行] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="fe205-102">Query Options Execution (General Page)</span></span>
  <span data-ttu-id="fe205-103">このページを使用して、クエリを実行するためのオプションを指定し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fe205-103">Use this page to specify the options for running [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="fe205-104">このダイアログ ボックスにアクセスするには、クエリ エディター ウィンドウ内で右クリックし、 **[クエリ オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe205-104">To access this dialog box, right-click the body of a Query Editor window, and then click **Query Options**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="fe205-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="fe205-105">UI element list</span></span>  
 <span data-ttu-id="fe205-106">**SET ROWCOUNT**</span><span class="sxs-lookup"><span data-stu-id="fe205-106">**SET ROWCOUNT**</span></span>  
 <span data-ttu-id="fe205-107">既定値の 0 は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] がすべての結果を受け取るまで待機することを意味します。</span><span class="sxs-lookup"><span data-stu-id="fe205-107">The default value of 0 indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will wait for results until all results are received.</span></span> <span data-ttu-id="fe205-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が指定された行数を取得した後にクエリを停止するように設定するには、0 より大きい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe205-108">Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to halt the query after obtaining the specified number of rows.</span></span> <span data-ttu-id="fe205-109">このオプションをオフにして、すべての行が返されるようにするには、SET ROWCOUNT 0 を指定してください。</span><span class="sxs-lookup"><span data-stu-id="fe205-109">To turn this option off (so that all rows are returned), specify SET ROWCOUNT 0.</span></span>  
  
 <span data-ttu-id="fe205-110">**SET TEXTSIZE**</span><span class="sxs-lookup"><span data-stu-id="fe205-110">**SET TEXTSIZE**</span></span>  
 <span data-ttu-id="fe205-111">既定値の 2,147,483,647 バイトは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が `text`、`ntext`、`nvarchar(max)`、および `varchar(max)` の各データ フィールドの上限まで、完全なデータ フィールドを提供することを示します。</span><span class="sxs-lookup"><span data-stu-id="fe205-111">The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will provide a complete data field up to the limit of `text`, `ntext`, `nvarchar(max)`, and `varchar(max)` data fields.</span></span> <span data-ttu-id="fe205-112">XML データ型は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="fe205-112">It does not affect the XML data type.</span></span> <span data-ttu-id="fe205-113">大きな値の場合に結果を制限するには、これより小さなサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="fe205-113">Provide a smaller number to limit results in the case of large values.</span></span> <span data-ttu-id="fe205-114">指定されたサイズよりも大きい列は切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="fe205-114">Columns greater than the number provided will be truncated.</span></span>  
  
 <span data-ttu-id="fe205-115">**[実行タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="fe205-115">**Execution time-out**</span></span>  
 <span data-ttu-id="fe205-116">クエリを取り消すまで待機する秒数を示します。</span><span class="sxs-lookup"><span data-stu-id="fe205-116">Indicates the number of seconds to wait before canceling the query.</span></span> <span data-ttu-id="fe205-117">値 0 は、待ち時間が無限 (タイムアウトなし) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="fe205-117">A value of 0 indicates an infinite wait, or no time-out.</span></span>  
  
 <span data-ttu-id="fe205-118">**[バッチ区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="fe205-118">**Batch separator**</span></span>  
 <span data-ttu-id="fe205-119">Transact-SQL ステートメントをバッチに分けるために使用する単語を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe205-119">Type a word that you use to separate Transact-SQL statements into batches.</span></span> <span data-ttu-id="fe205-120">既定値は GO です。</span><span class="sxs-lookup"><span data-stu-id="fe205-120">The default is GO.</span></span>  
  
 <span data-ttu-id="fe205-121">**[既定で、新しいクエリを SQLCMD モードで開始する]**</span><span class="sxs-lookup"><span data-stu-id="fe205-121">**By default, open new queries in SQLCMD Mode**</span></span>  
 <span data-ttu-id="fe205-122">新しいクエリを SQLCMD モードで開始するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fe205-122">Select this check box to open new queries in SQLCMD mode.</span></span> <span data-ttu-id="fe205-123">このチェック ボックスは、 **[ツール]** メニューからダイアログ ボックスを開いたときだけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe205-123">This check box is visible only when the dialog box is opened through the **Tools** menu.</span></span>  
  
 <span data-ttu-id="fe205-124">このオプションを選択する場合は、次の制限事項に注意してください。</span><span class="sxs-lookup"><span data-stu-id="fe205-124">When you select this option, be aware of the following limitations:</span></span>  
  
-   <span data-ttu-id="fe205-125">[!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディターの IntelliSense が無効になります。</span><span class="sxs-lookup"><span data-stu-id="fe205-125">IntelliSense in the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor is turned off.</span></span>  
  
-   <span data-ttu-id="fe205-126">クエリ エディターはコマンド ラインから実行できないため、変数などのコマンド ライン パラメーターを渡すことができません。</span><span class="sxs-lookup"><span data-stu-id="fe205-126">Because Query Editor does not run from the command line, you cannot pass in command-line parameters such as variables.</span></span>  
  
-   <span data-ttu-id="fe205-127">クエリ エディターはオペレーティング システムのプロンプトに応答できないため、対話型のステートメントを実行しないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe205-127">Because Query Editor cannot respond to operating-system prompts, you must be careful not to run interactive statements.</span></span>  
  
 <span data-ttu-id="fe205-128">**既定値にリセット**</span><span class="sxs-lookup"><span data-stu-id="fe205-128">**Reset to Default**</span></span>  
 <span data-ttu-id="fe205-129">このページ上のすべての値を元の既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="fe205-129">Resets all values on this page to the original default values.</span></span>  
  
  
