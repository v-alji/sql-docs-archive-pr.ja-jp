---
title: '[分析サーバーのプロパティ] ダイアログボックス (Analysis Services) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMSIMBI.SERVERPROPERTIES.F1
- SQL12.ASVS.SQLSERVERSTUDIO.SERVERPROPERTIES.F1
helpviewer_keywords:
- Analysis Server Properties dialog box
ms.assetid: b01ec658-c191-49c9-a6cb-549b21a368ab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6daef467782917d52fa00c6d236ce2d9305ab9e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633674"
---
# <a name="analysis-server-properties-dialog-box-analysis-services"></a><span data-ttu-id="b1c6c-102">[分析サーバーのプロパティ] ダイアログ ボックス (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b1c6c-102">Analysis Server Properties Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="b1c6c-103">**の** [分析サーバーのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスの全般的な設定、言語と照合順序の設定、およびセキュリティ設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-103">Use the **Analysis Server Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the general, language/collation, and security settings for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="b1c6c-104">**オブジェクト エクスプローラー** の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスを右クリックし、ショートカット メニューの **[プロパティ]** を選択することによって、 **[分析サーバーのプロパティ]** ダイアログ ボックスを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-104">You can display the **Analysis Server Properties** dialog box by right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance in **Object Explorer** and selecting **Properties** from the context menu.</span></span> <span data-ttu-id="b1c6c-105">**[分析サーバーのプロパティ]** ダイアログ ボックスには、次のプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-105">The **Analysis Server Properties** dialog box contains the following properties.</span></span>  
  
## <a name="information-properties"></a><span data-ttu-id="b1c6c-106">情報プロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-106">Information Properties</span></span>  
 <span data-ttu-id="b1c6c-107">このページを使用すると、サーバーのモード、バージョン、互換性レベルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-107">Use this page to view server mode, version, and compatibility level.</span></span> <span data-ttu-id="b1c6c-108">各インスタンスは、テーブル サーバー モードまたは多次元サーバー モードでインストールされ、テーブル モデルまたは多次元モデルを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-108">Each instance is installed in either Tabular or Multidimensional server mode, with the ability to load tabular or multidimensional models.</span></span> <span data-ttu-id="b1c6c-109">両方のモードをサポートする場合は、インスタンスを 2 つインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-109">If you need to support both modes, you must install two instances.</span></span>  
  
 <span data-ttu-id="b1c6c-110">**サポートされている互換性レベル**は、 `DefaultCompatibilityLevel` AMO のプロパティと同じです。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-110">**Supported Compatibility Level** is equivalent to the `DefaultCompatibilityLevel` property in AMO.</span></span> <span data-ttu-id="b1c6c-111">このプロパティは読み取り専用であり、インストール時に指定したサーバー配置モードに基づいています。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-111">It is read-only, based on the server deployment mode specified during installation.</span></span> <span data-ttu-id="b1c6c-112">サーバーのモードやバージョンによって異なる操作 (テーブル サーバー インスタンスにテーブル データベースのバックアップを復元する操作など) を実行するときに、サーバーでこのプロパティが確認されます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-112">The server checks this property when performing operations that vary by server mode or version, such as restoring a backup of a tabular database onto a tabular server instance.</span></span> <span data-ttu-id="b1c6c-113">テーブル モデルや多次元モデルのデータベース互換性モードと混同しないでください。名前と値が類似しているため注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-113">Do not confuse it with the database compatibility mode of tabular or multidimensional models, which have a similar names and values.</span></span> <span data-ttu-id="b1c6c-114">このサーバー プロパティの有効値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-114">Valid values for this server property include:</span></span>  
  
-   <span data-ttu-id="b1c6c-115">**1100** は、配置モード 0 に対する既定の互換性レベルです (多次元モードとデータ マイニング モードの場合)。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-115">**1100** is the default compatibility level for a deployment mode of 0, for multidimensional and data mining mode.</span></span>  
  
-   <span data-ttu-id="b1c6c-116">**1103** は、配置モード 1 または 2 に対する既定の互換性レベルです (テーブル モードや [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]をサポートするインストールの場合)。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-116">**1103** is the default compatibility level for deployment modes 1 or 2, for installations supporting Tabular mode or [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)].</span></span>  
  
 <span data-ttu-id="b1c6c-117">サーバーは、クライアントが名前空間の要求 DISCOVER_XML_METADATA をサポートしている場合に、この値を返します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-117">The server returns this value when a client supporting the namespace requests DISCOVER_XML_METADATA.</span></span> <span data-ttu-id="b1c6c-118">詳細については、「 [DISCOVER_XML_METADATA 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-118">See [DISCOVER_XML_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset) for more details.</span></span>  
  
## <a name="general-properties"></a><span data-ttu-id="b1c6c-119">全般プロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-119">General Properties</span></span>  
 <span data-ttu-id="b1c6c-120">このページを使用して、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのフォルダーの場所、ネットワークの設定など、基本および詳細な全般的プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-120">Use this page to set the basic and advanced general properties, such as folder locations and network settings, for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="b1c6c-121">サーバーのプロパティ ページには、管理者が変更する可能性が高いプロパティのみが表示されます。こうしたプロパティには、サーバーをチューニングして構成するためのメモリ プールやスレッド プールのプロパティなどがあります。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-121">The server properties page shows only those properties an administrator is more likely to change, such as memory and thread pool properties used to tune the server for certain configurations.</span></span> <span data-ttu-id="b1c6c-122">主要なプロパティ グループへのリンクを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-122">The following list provides links to the main property groups:</span></span>  
  
-   [<span data-ttu-id="b1c6c-123">全般プロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-123">General Properties</span></span>](server-properties/general-properties.md)  
  
-   [<span data-ttu-id="b1c6c-124">データマイニングプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-124">Data Mining Properties</span></span>](server-properties/data-mining-properties.md)  
  
-   [<span data-ttu-id="b1c6c-125">Feature プロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-125">Feature Properties</span></span>](server-properties/feature-properties.md)  
  
-   [<span data-ttu-id="b1c6c-126">Filestore のプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-126">Filestore Properties</span></span>](server-properties/filestore-properties.md)  
  
-   [<span data-ttu-id="b1c6c-127">ロックマネージャーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-127">Lock Manager Properties</span></span>](server-properties/lock-manager-properties.md)  
  
-   [<span data-ttu-id="b1c6c-128">ログのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-128">Log Properties</span></span>](server-properties/log-properties.md)  
  
-   [<span data-ttu-id="b1c6c-129">メモリのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-129">Memory Properties</span></span>](server-properties/memory-properties.md)  
  
-   [<span data-ttu-id="b1c6c-130">ネットワークのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-130">Network Properties</span></span>](server-properties/network-properties.md)  
  
-   [<span data-ttu-id="b1c6c-131">OLAP のプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-131">OLAP Properties</span></span>](server-properties/olap-properties.md)  
  
-   [<span data-ttu-id="b1c6c-132">セキュリティのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-132">Security Properties</span></span>](server-properties/security-properties.md)  
  
-   [<span data-ttu-id="b1c6c-133">スレッドプールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-133">Thread Pool Properties</span></span>](server-properties/thread-pool-properties.md)  
  
## <a name="language-collation-properties"></a><span data-ttu-id="b1c6c-134">言語/照合順序プロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-134">Language Collation Properties</span></span>  
 <span data-ttu-id="b1c6c-135">このページを使用して、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の既定の言語および照合順序のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-135">Use this page to set the default language and collation options for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b1c6c-136">次に、各オプションの簡単な説明を示します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-136">The following list contains short descriptions of each option.</span></span> <span data-ttu-id="b1c6c-137">詳細については、「 [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-137">See [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) for more detailed descriptions.</span></span>  
  
-   <span data-ttu-id="b1c6c-138">**[バイナリ]** 。このオプションを使用すると、文字ごとに定義されたビット パターンに基づいてデータの並べ替えと比較を行います。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-138">**Binary** is used to sort and compare data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="b1c6c-139">バイナリの並べ替え順では大文字と小文字が区別されるため、小文字は大文字より前に配置されます。また、アクセントも区別されます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-139">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="b1c6c-140">これは、最速の並べ替え順です。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-140">This is the fastest sorting order.</span></span>  
  
     <span data-ttu-id="b1c6c-141">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には関連する言語またはアルファベットの辞書で定義されている並べ替えおよび比較ルールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-141">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] follows sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b1c6c-142">このオプションが選択されている場合、 **[大文字と小文字を区別する]**、 **[アクセントを区別する]**、 **[かなを区別する]**、および **[文字幅を区別する]** オプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-142">If this option is selected, the **Case-Sensitive**, **Accent-Sensitive**, **Kana-Sensitive**, and **Width-Sensitive** options are disabled.</span></span>  
  
-   <span data-ttu-id="b1c6c-143">**[バイナリ 2]** 。このオプションを使用すると、文字ごとに定義されたビット パターンに基づいて Unicode データの並べ替えと比較を行います。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-143">**Binary 2** is used to sort and compare Unicode data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="b1c6c-144">バイナリの並べ替え順では大文字と小文字が区別されるため、小文字は大文字より前に配置されます。また、アクセントも区別されます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-144">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="b1c6c-145">これは、最速の並べ替え順です。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-145">This is the fastest sorting order.</span></span>  
  
-   <span data-ttu-id="b1c6c-146">**[大文字と小文字を区別する]** を使用すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、大文字と小文字による区別を行います。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-146">**Case-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between uppercase and lowercase letters.</span></span>  
  
     <span data-ttu-id="b1c6c-147">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は大文字と小文字を区別しません。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-147">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the uppercase and lowercase versions of letters to be equal.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="b1c6c-148">大文字と小文字を区別するかどうかは、大文字小文字を**区別**するかどうかを定義しません。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-148">does not define whether lowercase letters sort lower or higher in relation to uppercase letters when **Case-sensitive** is not selected.</span></span>  
  
-   <span data-ttu-id="b1c6c-149">**[アクセントを区別する]** を使用すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、アクセント符号が付いた文字と付いていない文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-149">**Accent-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between accented and unaccented characters.</span></span> <span data-ttu-id="b1c6c-150">たとえば、'a' と '&#xE1;' は等しくありません。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-150">For example, 'a' is not equal to 'á'.</span></span>  
  
     <span data-ttu-id="b1c6c-151">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] はアクセント符号の付いた文字と付いていない文字を同じものと見なします。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-151">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the accented and unaccented versions of letters to be equal.</span></span>  
  
-   <span data-ttu-id="b1c6c-152">**[かなを区別する]** を使用すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、ひらがなとカタカナという日本語の 2 種類のかな文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-152">**Kana-Sensitive** is used to and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between the two types of Japanese kana characters: Hiragana and Katakana.</span></span>  
  
     <span data-ttu-id="b1c6c-153">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] はひらがなとカタカナを同じものと見なします。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-153">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers Hiragana and Katakana characters to be equal.</span></span>  
  
-   <span data-ttu-id="b1c6c-154">**[文字幅を区別する]** を使用すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、1 バイト文字 (半角文字) と同じ文字の 2 バイト表現 (全角文字) とを区別します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-154">**Width-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between a single-byte character (half-width) and the same character when represented as a double-byte character (full-width).</span></span>  
  
     <span data-ttu-id="b1c6c-155">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は同じ文字の 1 バイト表現と 2 バイト表現を同じものと見なします。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-155">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the single-byte and double-byte representation of the same character to be equal.</span></span>  
  
## <a name="security-properties"></a><span data-ttu-id="b1c6c-156">セキュリティのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1c6c-156">Security Properties</span></span>  
 <span data-ttu-id="b1c6c-157">このページを使用して、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー管理者ロールに所属する Windows ユーザー アカウントとグループ アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-157">Use this page to specify the Windows user and group accounts belonging to the server administrator role for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="b1c6c-158">このロールのメンバーシップによって、サーバー全体のタスク (データベースの作成や処理、サーバーのプロパティの変更、このロールの他のメンバーシップの追加や削除、トレースの起動など) を実行するための権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-158">Membership in this role conveys permission to perform server-wide tasks, such as creating or processing a database, modifying server properties, adding or removing other members of this role, or launching a trace.</span></span> <span data-ttu-id="b1c6c-159">詳細については、 [&#40;Analysis Services&#41;にサーバー管理者権限を付与](instances/grant-server-admin-rights-to-an-analysis-services-instance.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1c6c-159">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c6c-160">参照</span><span class="sxs-lookup"><span data-stu-id="b1c6c-160">See Also</span></span>  
 <span data-ttu-id="b1c6c-161">[Analysis Services インスタンスのサーバーモードの決定](instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="b1c6c-161">[Determine the Server Mode of an Analysis Services Instance](instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="b1c6c-162">[Analysis Services でのサーバープロパティの構成](server-properties/server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b1c6c-162">[Configure Server Properties in Analysis Services](server-properties/server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="b1c6c-163">[Analysis Services によってサポートされる認証方法](instances/authentication-methodologies-supported-by-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b1c6c-163">[Authentication methodologies supported by Analysis Services](instances/authentication-methodologies-supported-by-analysis-services.md) </span></span>  
 <span data-ttu-id="b1c6c-164">[ロールとアクセス許可 &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b1c6c-164">[Roles and Permissions &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="b1c6c-165">言語および照合順序 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b1c6c-165">Languages and Collations &#40;Analysis Services&#41;</span></span>](languages-and-collations-analysis-services.md)  
  
  
