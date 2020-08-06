---
title: データ フロー内のデータ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- comparing data
- data types [Integration Services], data flow
- parsing [Integration Services]
- string comparisons
- data flow [Integration Services], data options
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a073db65768c413b6cbe648c757ad75d80bd318e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741153"
---
# <a name="data-in-data-flows"></a><span data-ttu-id="01726-102">データ フロー内のデータ</span><span class="sxs-lookup"><span data-stu-id="01726-102">Data in Data Flows</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="01726-103">には、データ フローで使用するデータ型のセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="01726-103">provides a set of data types that are used in data flows.</span></span>  
  
## <a name="data-type-conversion"></a><span data-ttu-id="01726-104">データ型の変換</span><span class="sxs-lookup"><span data-stu-id="01726-104">Data Type Conversion</span></span>  
 <span data-ttu-id="01726-105">データ フローに追加する変換元は、変換元のデータを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="01726-105">The source that you add to a data flow converts the source data to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types.</span></span> <span data-ttu-id="01726-106">後続の変換では、データを別の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のデータ型に変換できます。また、データの読み込み先となるデータ ストアの型によっては、変換先は、最後の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のデータ型を、変換先のデータ ストアで必要なデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="01726-106">Subsequent transformations may convert the data to different [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, and depending on the type of data store into which data is loaded, destinations may convert the final [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the data type required by the destination data store.</span></span> <span data-ttu-id="01726-107">詳細については、「 [Integration Services Data Types](integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01726-107">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="01726-108">データを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のデータ型に変換するために、データ フロー コンポーネントはデータを解析します。</span><span class="sxs-lookup"><span data-stu-id="01726-108">To convert the data to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type, a data flow component parses the data.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="01726-109">には、高速解析と標準解析という 2 種類のデータ解析が用意されています。</span><span class="sxs-lookup"><span data-stu-id="01726-109">provides two types of data parsing: fast parse and standard parse.</span></span> <span data-ttu-id="01726-110">ほとんどのデータ フロー コンポーネントで使用できるのは、標準解析のみです。ただし、フラット ファイルの変換元とデータ変換の変換では、高速解析と標準解析のどちらも使用できます。</span><span class="sxs-lookup"><span data-stu-id="01726-110">Most data flow components can use only standard parsing; however, the Flat File source and the Data Conversion transformation can use either fast parse or standard parse.</span></span> <span data-ttu-id="01726-111">詳細については、「 [データの解析](parsing-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01726-111">For more information, see [Parsing Data](parsing-data.md).</span></span>  
  
## <a name="data-type-comparison"></a><span data-ttu-id="01726-112">データ型の比較</span><span class="sxs-lookup"><span data-stu-id="01726-112">Data Type Comparison</span></span>  
 <span data-ttu-id="01726-113">多くの変換は、データ値を比較します。</span><span class="sxs-lookup"><span data-stu-id="01726-113">Many transformations compare data values.</span></span> <span data-ttu-id="01726-114">たとえば、集計変換はデータ行セットの値を集計する目的で値を比較し、並べ替え変換は値を並べ替える目的で値を比較します。また、参照変換は、データ値を別の参照テーブルにある値と比較します。</span><span class="sxs-lookup"><span data-stu-id="01726-114">For example, the Aggregate transformation compares values for the purpose of aggregating values across a set of data rows, the Sort transformation compares values in order to sort them, and the Lookup transformation compares values against values in a separate reference table.</span></span> <span data-ttu-id="01726-115">文字列を比較する方法を指定するため、変換には比較オプションのセットが含まれています。比較オプションには、大文字と小文字を区別するかどうか、日本語テキストでかなの種類をどのように処理するのか、文字列内の空白文字を無視するかどうか、などを指定するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="01726-115">To specify how strings should be compared, the transformation includes a set of comparison options such as whether to ignore case sensitivity, how to handle kana types in Japanese text, and whether to ignore white-space characters in the string.</span></span> <span data-ttu-id="01726-116">詳しくは、「 [Comparing String Data](comparing-string-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="01726-116">For more information, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="01726-117">式エバリュエーターも、変数、優先順位制約、および変換が使用する式を評価する際に、データ値を比較します。</span><span class="sxs-lookup"><span data-stu-id="01726-117">The expression evaluator also compares data values when it evaluates the expressions that variables, precedence constraints, and transformations use.</span></span>  
  
## <a name="data-flow-troubleshooting"></a><span data-ttu-id="01726-118">データ フローのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="01726-118">Data Flow Troubleshooting</span></span>  
 <span data-ttu-id="01726-119">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログにパッケージを配置したら、実行時にパッケージのデータ フローを分析して、パフォーマンスを確認したり、他の問題を見つけたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="01726-119">Once you have deployed a package to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog, you can analyze the data flow in the package during execution to check performance or look for other issues.</span></span> <span data-ttu-id="01726-120">パッケージの状態と履歴を表示できる標準レポートを利用できます。また、パッケージ実行に関する詳細情報を提供するデータベース ビューに対してクエリを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="01726-120">Standard reports are available that allow you to view package status and history, and you can query database views that provide detailed information about package execution.</span></span> <span data-ttu-id="01726-121">実行時にデータ タップを動的に追加および削除して、パッケージの特定のコンポーネントをターゲットとすることもできます。</span><span class="sxs-lookup"><span data-stu-id="01726-121">You also can dynamically add and remove data taps during execution to target specific components of your package.</span></span> <span data-ttu-id="01726-122">詳細については、「 [データ フローの解析](data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01726-122">For more information, see [Analysis of Data Flow](data-flow.md).</span></span>  
  
  
