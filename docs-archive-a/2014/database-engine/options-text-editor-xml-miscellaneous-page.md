---
title: '[オプション] ([テキストエディター]/[XML]/[その他] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1a9509f0-c663-4b31-b396-7f5dc4371651
author: rothja
ms.author: jroth
ms.openlocfilehash: d937368d30122442ccbc40372a6b8e1cabc141e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711009"
---
# <a name="options-text-editor---xml---miscellaneous-page"></a><span data-ttu-id="cef4a-102">[オプション] ([テキスト エディター]/[XML]/[その他] ページ)</span><span class="sxs-lookup"><span data-stu-id="cef4a-102">Options (Text Editor - XML - Miscellaneous Page)</span></span>

<span data-ttu-id="cef4a-103">**[オプション]** ダイアログ ボックスを使用すると、XML エディターのオートコンプリートとスキーマの設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="cef4a-103">The **Options** dialog box lets you change the autocompletion and schema settings for the XML Editor.</span></span> <span data-ttu-id="cef4a-104">この設定を変更するには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[テキスト エディター]** フォルダーを展開して、 **[XML]** 、 **[その他]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="cef4a-104">These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, click **XML** and then click **Miscellaneous** .</span></span>  
  
## <a name="auto-insert"></a><span data-ttu-id="cef4a-105">自動挿入</span><span class="sxs-lookup"><span data-stu-id="cef4a-105">Auto Insert</span></span>  
 <span data-ttu-id="cef4a-106">**終了タグ**</span><span class="sxs-lookup"><span data-stu-id="cef4a-106">**Close tags**</span></span>  
 <span data-ttu-id="cef4a-107">テキスト エディターで XML 要素を記述する際に、終了タグが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="cef4a-107">The Text Editor adds close tags when authoring XML elements.</span></span> <span data-ttu-id="cef4a-108">要素の開始タグが選択されると、対応する終了タグが挿入されます。この場合、対応する名前空間プレフィックスも含められます。</span><span class="sxs-lookup"><span data-stu-id="cef4a-108">If an element start tag is selected, the editor inserts the matching close tag, including a matching namespace prefix.</span></span> <span data-ttu-id="cef4a-109">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="cef4a-109">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="cef4a-110">**属性値の引用符**</span><span class="sxs-lookup"><span data-stu-id="cef4a-110">**Attribute quotes**</span></span>  
 <span data-ttu-id="cef4a-111">XML 属性を記述する際に、自動的に `="``"` が挿入され、カレット (**^** ) が引用符の内側に置かれます。</span><span class="sxs-lookup"><span data-stu-id="cef4a-111">When authoring XML attributes, the editor inserts the `="``"` characters and positions the caret (**^)** inside the quotation marks.</span></span> <span data-ttu-id="cef4a-112">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="cef4a-112">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="cef4a-113">**名前空間の宣言**</span><span class="sxs-lookup"><span data-stu-id="cef4a-113">**Namespace declarations**</span></span>  
 <span data-ttu-id="cef4a-114">名前空間の宣言が必要な場所には、自動的に宣言が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="cef4a-114">The editor automatically inserts namespace declarations wherever they are needed.</span></span> <span data-ttu-id="cef4a-115">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="cef4a-115">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="cef4a-116">**[その他のマークアップ (コメント、CDATA)]**</span><span class="sxs-lookup"><span data-stu-id="cef4a-116">**Other markup (Comments, CDATA)**</span></span>  
 <span data-ttu-id="cef4a-117">コメント、CDATA、DOCTYPE、処理命令、その他のマークアップがオートコンプリートされます。</span><span class="sxs-lookup"><span data-stu-id="cef4a-117">Comments, CDATA, DOCTYPE, processing instructions, and other markup is autocompleted.</span></span> <span data-ttu-id="cef4a-118">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="cef4a-118">This check box is selected by default.</span></span>  
  
## <a name="network"></a><span data-ttu-id="cef4a-119">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="cef4a-119">Network</span></span>  
 <span data-ttu-id="cef4a-120">**[DTD とスキーマを自動的にダウンロードする]**</span><span class="sxs-lookup"><span data-stu-id="cef4a-120">**Automatically download DTDs and schemas**</span></span>  
 <span data-ttu-id="cef4a-121">スキーマと DTD (Document Type Definition) は HTTP ロケーションから自動的にダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="cef4a-121">Schemas and document type definitions (DTDs) are automatically downloaded from HTTP locations.</span></span> <span data-ttu-id="cef4a-122">この機能では、自動プロキシ サーバー検出が有効な System.Net を使用します。</span><span class="sxs-lookup"><span data-stu-id="cef4a-122">This feature uses System.Net with autoproxy server detection enabled.</span></span> <span data-ttu-id="cef4a-123">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="cef4a-123">This check box is selected by default.</span></span>  
  
## <a name="outlining"></a><span data-ttu-id="cef4a-124">アウトライン</span><span class="sxs-lookup"><span data-stu-id="cef4a-124">Outlining</span></span>  
 <span data-ttu-id="cef4a-125">**ファイルが開かれたときにアウトライン モードを実行する**</span><span class="sxs-lookup"><span data-stu-id="cef4a-125">**Enter outlining mode when files open**</span></span>  
 <span data-ttu-id="cef4a-126">ファイルが開いているときにアウトライン機能をオンにします。</span><span class="sxs-lookup"><span data-stu-id="cef4a-126">Turns on the outlining feature when a file is opened.</span></span> <span data-ttu-id="cef4a-127">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="cef4a-127">This check box is selected by default.</span></span>  
  
## <a name="caching"></a><span data-ttu-id="cef4a-128">キャッシュ</span><span class="sxs-lookup"><span data-stu-id="cef4a-128">Caching</span></span>  
 <span data-ttu-id="cef4a-129">**スキーマ**</span><span class="sxs-lookup"><span data-stu-id="cef4a-129">**Schemas**</span></span>  
 <span data-ttu-id="cef4a-130">スキーマ キャッシュの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="cef4a-130">Specifies the location of the schema cache.</span></span> <span data-ttu-id="cef4a-131">[...] ボタンをクリックすると、現在のスキーマ キャッシュの場所が新しいウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cef4a-131">The Browse button (...) opens the current schema cache location in a new window.</span></span> <span data-ttu-id="cef4a-132">既定の場所は、 *\<Management Studio install directory>* \ Xml\ schemasです。</span><span class="sxs-lookup"><span data-stu-id="cef4a-132">The default location is *\<Management Studio install directory>* \Xml\Schemas.</span></span>  
