---
title: IntelliSense のトラブルシューティング
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- unavailable options [IntelliSense]
- IntelliSense [SQL Server], troubleshooting
- IntelliSense [SQL Server], unavailable options
- troubleshooting [IntelliSense]
ms.assetid: 4b72ffc6-aea2-4e11-ab36-fa2de4d7bcc5
author: rothja
ms.author: jroth
ms.openlocfilehash: 087baf616fc215c480ae78621623cbe1ed512b57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717751"
---
# <a name="troubleshooting-intellisense-sql-server-management-studio"></a><span data-ttu-id="ecf2a-102">IntelliSense のトラブルシューティング (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ecf2a-102">Troubleshooting IntelliSense (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ecf2a-103">IntelliSense オプションが正しく機能しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-103">There are certain cases when the IntelliSense options might not work as you expect.</span></span>  
  
## <a name="conditions-that-affect-intellisense"></a><span data-ttu-id="ecf2a-104">IntelliSense が影響を受ける状況</span><span class="sxs-lookup"><span data-stu-id="ecf2a-104">Conditions That Affect IntelliSense</span></span>  
 <span data-ttu-id="ecf2a-105">次の場合に IntelliSense の動作が影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-105">The following conditions might affect the behavior of IntelliSense:</span></span>  
  
-   <span data-ttu-id="ecf2a-106">カーソルよりも上にコード エラーがある場合</span><span class="sxs-lookup"><span data-stu-id="ecf2a-106">There is a code error above the cursor.</span></span>  
  
     <span data-ttu-id="ecf2a-107">挿入ポイントの位置よりも上に不完全なステートメントや他のコーディング エラーがあると、IntelliSense は、コードの要素を解析できないので正しく機能しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-107">If there is an incomplete statement or other coding error above the location of the insertion point, IntelliSense may be unable to parse the code elements, and therefore will not work.</span></span> <span data-ttu-id="ecf2a-108">IntelliSense を再び有効にするために、該当するコードをコメント化できます。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-108">You can comment out the applicable code to enable IntelliSense again.</span></span>  
  
-   <span data-ttu-id="ecf2a-109">コードのコメント内に挿入ポイントがある場合</span><span class="sxs-lookup"><span data-stu-id="ecf2a-109">The insertion point is inside a code comment.</span></span>  
  
     <span data-ttu-id="ecf2a-110">挿入ポイントがソース ファイルのコメント内にある場合は、IntelliSense オプションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-110">IntelliSense options are not available when the insertion point is within a comment in your source file.</span></span>  
  
-   <span data-ttu-id="ecf2a-111">文字列リテラル内に挿入ポイントがある場合</span><span class="sxs-lookup"><span data-stu-id="ecf2a-111">The insertion point is inside a string literal.</span></span>  
  
     <span data-ttu-id="ecf2a-112">挿入ポイントが引用符で囲んだ文字列リテラル内にある場合は、IntelliSense オプションを使用できません。以下はその例です。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-112">IntelliSense options are not available when the insertion point is inside the quotation marks around a string literal, for example:</span></span>  
  
     `WHERE FirstName LIKE 'Patri%|'`  
  
-   <span data-ttu-id="ecf2a-113">自動オプションがオフになっている場合</span><span class="sxs-lookup"><span data-stu-id="ecf2a-113">The automatic options are turned off.</span></span>  
  
     <span data-ttu-id="ecf2a-114">既定では、IntelliSense の多くの機能が自動的に実行されるようになっていますが、各機能を無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-114">Many IntelliSense features work automatically by default, but you can disable any feature.</span></span>  
  
     <span data-ttu-id="ecf2a-115">自動入力候補機能を無効にしている場合でも、IntelliSense 機能を使用することは可能です。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-115">Even when automatic statement completion is disabled, you can use an IntelliSense feature.</span></span> <span data-ttu-id="ecf2a-116">詳細については、「[IntelliSense の構成 &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-116">For more information, see [Configure IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).</span></span>  
  
## <a name="database-engine-query-intellisense"></a><span data-ttu-id="ecf2a-117">データベース エンジン クエリの IntelliSense</span><span class="sxs-lookup"><span data-stu-id="ecf2a-117">Database Engine Query IntelliSense</span></span>  
 <span data-ttu-id="ecf2a-118">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディターに関しては、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-118">The following issues apply to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Query Editor:</span></span>  
  
-   <span data-ttu-id="ecf2a-119">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターの IntelliSense 機能では、すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文要素がサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-119">The IntelliSense functionality of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor does not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax elements.</span></span> <span data-ttu-id="ecf2a-120">パラメーターのヘルプでは、拡張ストアド プロシージャなど、一部のオブジェクトのパラメーターがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-120">Parameter help does not support the parameters in some objects, such as extended stored procedures.</span></span> <span data-ttu-id="ecf2a-121">詳細については、「 [IntelliSense でサポートされている Transact-SQL 構文](transact-sql-syntax-supported-by-intellisense.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-121">For more information, see [Transact-SQL Syntax Supported by IntelliSense](transact-sql-syntax-supported-by-intellisense.md).</span></span>  
  
-   <span data-ttu-id="ecf2a-122">IntelliSense は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディターが [!INCLUDE[ssDE](../../includes/ssde-md.md)] 以降の [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] のインスタンスに接続されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-122">IntelliSense is only available when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span> <span data-ttu-id="ecf2a-123">Intellisense は、クエリ エディターが以前のバージョンの [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続されているときは使用できません。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-123">IntelliSense is not available when the Query Editor is connected to earlier versions of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="ecf2a-124">SQLCMD モードを有効にすると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターの IntelliSense が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-124">IntelliSense is turned off in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor when the SQLCMD mode is set on.</span></span>  
  
-   <span data-ttu-id="ecf2a-125">IntelliSense 機能は、現在のエディター ウィンドウがデータベースに接続された後に別の接続で作成されたデータベース オブジェクトには対応していません。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-125">IntelliSense functionality does not cover database objects created by another connection after your editor window connected to the database.</span></span> <span data-ttu-id="ecf2a-126">入力候補一覧などの IntelliSense 機能からオブジェクトが欠落している場合、エディター ウィンドウのオブジェクトのキャッシュを更新するには、次の 3 つのメカニズムのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-126">If objects are missing from IntelliSense features such as completion lists, you can choose one of these three mechanisms to refresh the cache of objects for your editor window:</span></span>  
  
    -   <span data-ttu-id="ecf2a-127">**[編集]** メニューの **[IntelliSense]** をポイントし、 **[ローカル キャッシュの更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-127">Select the **Edit** menu, select **IntelliSense**, then select **Refresh Local Cache**.</span></span>  
  
    -   <span data-ttu-id="ecf2a-128">Ctrl</localizedText> キーと <localizedText>Shift</localizedText> キーを押しながら <localizedText>R</localizedText> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-128">Use the CTRL+Shift+R keyboard shortcut.</span></span>  
  
    -   <span data-ttu-id="ecf2a-129">現在のエディター ウィンドウを [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスから切断して再接続します。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-129">Disconnect your editor window from the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and reconnect.</span></span>  
  
-   <span data-ttu-id="ecf2a-130">権限のないデータベース オブジェクトは入力候補一覧に表示されません。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-130">Completion lists do not include database objects for which you do not have permissions.</span></span> <span data-ttu-id="ecf2a-131">IntelliSense は、権限のあるオブジェクトへの参照にフラグを付けます。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-131">IntelliSense flags references to objects for which you do have permissions.</span></span> <span data-ttu-id="ecf2a-132">たとえば、別のユーザーが記述したスクリプトを開いた場合、そのユーザーには権限があるものの自分には権限のないオブジェクトへの参照には無効のフラグが付けられます。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-132">For example, if you open a script that is written by someone else, any references to objects for which that person has permissions and you do not are flagged as incorrect.</span></span>  
  
-   <span data-ttu-id="ecf2a-133">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスへの接続が失われると、入力候補一覧が機能しなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-133">Completion lists might stop working if you lose the connection to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="ecf2a-134">インスタンスに再接続してください。</span><span class="sxs-lookup"><span data-stu-id="ecf2a-134">Reconnect to the instance.</span></span>  
  
  
