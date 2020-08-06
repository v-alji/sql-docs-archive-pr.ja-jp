---
title: サーバーの構成-Collation |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- collation configuration, SQL Server
- collation configuration, Setup
- collation configuration
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d06735590d23da6e91151202dd421639ea433b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643092"
---
# <a name="server-configuration---collation"></a><span data-ttu-id="b4347-102">サーバーの構成 - 照合順序</span><span class="sxs-lookup"><span data-stu-id="b4347-102">Server Configuration - Collation</span></span>
  <span data-ttu-id="b4347-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの [サーバーの構成 - 照合順序] ページでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で並べ替えに使用される照合順序の設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="b4347-103">On the Server Configuration - Collation page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard, you can modify collation settings that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] use for sorting purposes.</span></span> <span data-ttu-id="b4347-104">インストールされている別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、または別のコンピューターと照合順序設定を一致させるにはこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b4347-104">Select the option to match collation settings of different installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or of another computer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4347-105">Options</span><span class="sxs-lookup"><span data-stu-id="b4347-105">Options</span></span>  
 <span data-ttu-id="b4347-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="b4347-106">Customize for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b4347-107">の照合順序には、Windows 照合順序と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序という 2 種類のグループがあります。</span><span class="sxs-lookup"><span data-stu-id="b4347-107">provides two groups of collations: Windows collations and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span> <span data-ttu-id="b4347-108">[!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に異なる照合順序の設定を指定できます。また、両方に同じ照合順序を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b4347-108">You can specify separate collation settings for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], or you can specify the same collation for both.</span></span>  
  
 <span data-ttu-id="b4347-109">既定では、英語 (米国) システム ロケールには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序が選択されます。</span><span class="sxs-lookup"><span data-stu-id="b4347-109">By default, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collation is selected for US-English system locales.</span></span> <span data-ttu-id="b4347-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の他言語バージョンの既定の照合順序は、使用しているコンピューターの Windows システム ロケール設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="b4347-110">The default collation for localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is determined by the Windows system locale setting for your computer.</span></span>  
  
 <span data-ttu-id="b4347-111">既定の設定は、このインストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の照合順序の設定を別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスで使用される照合順序の設定に一致させる必要がある場合、または別のコンピューターの Windows システム ロケールに一致させる必要がある場合にのみ、変更するようにします。</span><span class="sxs-lookup"><span data-stu-id="b4347-111">The default settings should be changed only if the collation setting for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must match the collation settings used by another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or if it must match the Windows system locale of another computer.</span></span>  
  
 <span data-ttu-id="b4347-112">**注:** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は Windows 照合順序のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="b4347-112">**Note** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses Windows collations only.</span></span> <span data-ttu-id="b4347-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインストールを予定する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時に Windows 照合順序を選択して、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で一貫した結果が得られるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="b4347-113">If you plan to install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], select a Windows collation during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to ensure consistent results between the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b4347-114">詳細については、「 [セットアップでの照合順序の設定](https://go.microsoft.com/fwlink/?LinkId=190977)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4347-114">For more information, see [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="b4347-115">推奨する運用方法</span><span class="sxs-lookup"><span data-stu-id="b4347-115">Best Practices</span></span>  
 <span data-ttu-id="b4347-116">Windows システム ロケールと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップで使用される既定の照合順序との対応表については、「 [セットアップでの照合順序の設定](https://go.microsoft.com/fwlink/?LinkId=190977)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4347-116">For more information about a table of Windows System locales and the corresponding default collations used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, see [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977).</span></span>  
  
 <span data-ttu-id="b4347-117">可能であれば、組織で単一の照合順序を使用してください。</span><span class="sxs-lookup"><span data-stu-id="b4347-117">If it is possible, use a single collation for your organization.</span></span> <span data-ttu-id="b4347-118">そうすれば、データベース、列、式、または識別子ごとに照合順序を明示的に指定する必要はなくなります。</span><span class="sxs-lookup"><span data-stu-id="b4347-118">This way, you do not have to explicitly specify the collation for every database, column, expression, or identifier.</span></span> <span data-ttu-id="b4347-119">複数の照合順序とコード ページ設定を操作する必要がある場合は、照合順序の優先順位の規則を考慮してクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4347-119">If you must work with multiple collations and code page settings, code your queries to consider the rules of collation precedence.</span></span> <span data-ttu-id="b4347-120">詳細については、オンライン ブックの「[照合順序の優先順位 &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4347-120">For more information, see the Books Online topic for [Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql).</span></span>  
  
 <span data-ttu-id="b4347-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の照合順序を選択する場合は、次の推奨設定を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="b4347-121">When you select a collation for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consider the following recommendations:</span></span>  
  
-   <span data-ttu-id="b4347-122">バイナリ コード ポイント順が使用できる場合は、バイナリ 2 照合順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4347-122">Select a BINARY2 collation if binary code point based ordering is acceptable.</span></span>  
  
-   <span data-ttu-id="b4347-123">データ型間の比較で一貫性を保つには、Windows 照合順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4347-123">Select a Windows collation for consistent comparison across data types.</span></span>  
  
-   <span data-ttu-id="b4347-124">言語の並べ替えのサポートを向上させるには、新しい 100 レベルの照合順序を使用します。</span><span class="sxs-lookup"><span data-stu-id="b4347-124">Use a new 100-level collation for better linguistic sorting support.</span></span> <span data-ttu-id="b4347-125">詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4347-125">For more information, see [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="b4347-126">アップグレード済みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにデータベースを移行する場合は、データベースの既存の照合順序と一致する照合順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4347-126">If you plan to migrate a database to the upgraded instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select the collation that matches your existing collation of the database.</span></span>  
  
  
