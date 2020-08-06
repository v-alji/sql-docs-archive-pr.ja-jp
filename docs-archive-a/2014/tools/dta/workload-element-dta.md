---
title: ワークロード要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20184760c3fcb5eed6c02b8f8fd9b63f5586c9af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639847"
---
# <a name="workload-element-dta"></a><span data-ttu-id="e6e60-102">Workload 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e6e60-102">Workload Element (DTA)</span></span>
  <span data-ttu-id="e6e60-103">チューニング セッションで使用するワークロードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6e60-103">Specifies the workload to be used for a tuning session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e60-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6e60-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="e6e60-105">要素の特性</span><span class="sxs-lookup"><span data-stu-id="e6e60-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="e6e60-106">特徴</span><span class="sxs-lookup"><span data-stu-id="e6e60-106">Characteristic</span></span>|<span data-ttu-id="e6e60-107">説明</span><span class="sxs-lookup"><span data-stu-id="e6e60-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e6e60-108">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="e6e60-108">**Data type and length**</span></span>|<span data-ttu-id="e6e60-109">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e6e60-109">None.</span></span>|  
|<span data-ttu-id="e6e60-110">**既定値**</span><span class="sxs-lookup"><span data-stu-id="e6e60-110">**Default value**</span></span>|<span data-ttu-id="e6e60-111">[なし] :</span><span class="sxs-lookup"><span data-stu-id="e6e60-111">None.</span></span>|  
|<span data-ttu-id="e6e60-112">**個数**</span><span class="sxs-lookup"><span data-stu-id="e6e60-112">**Occurrence**</span></span>|<span data-ttu-id="e6e60-113">`DTAInput` 要素につき 1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="e6e60-113">Required once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e6e60-114">要素の関係</span><span class="sxs-lookup"><span data-stu-id="e6e60-114">Element Relationships</span></span>  
  
|<span data-ttu-id="e6e60-115">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="e6e60-115">Relationship</span></span>|<span data-ttu-id="e6e60-116">要素</span><span class="sxs-lookup"><span data-stu-id="e6e60-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e6e60-117">**親要素**</span><span class="sxs-lookup"><span data-stu-id="e6e60-117">**Parent element**</span></span>|[<span data-ttu-id="e6e60-118">データベース エンジン チューニング アドバイザーの起動および使用</span><span class="sxs-lookup"><span data-stu-id="e6e60-118">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|<span data-ttu-id="e6e60-119">**子要素**</span><span class="sxs-lookup"><span data-stu-id="e6e60-119">**Child elements**</span></span>|[<span data-ttu-id="e6e60-120">File 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e6e60-120">File Element &#40;DTA&#41;</span></span>](file-element-dta.md)<br /><br /> [<span data-ttu-id="e6e60-121">Workload の Database 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e6e60-121">Database Element for Workload &#40;DTA&#41;</span></span>](database-element-for-workload-dta.md)<br /><br /> [<span data-ttu-id="e6e60-122">EventString 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="e6e60-122">EventString Element &#40;DTA&#41;</span></span>](eventstring-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="e6e60-123">解説</span><span class="sxs-lookup"><span data-stu-id="e6e60-123">Remarks</span></span>  
 <span data-ttu-id="e6e60-124">ワークロードとは、チューニングするデータベースに対して実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのセットです。</span><span class="sxs-lookup"><span data-stu-id="e6e60-124">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="e6e60-125">データベース エンジン チューニング アドバイザーは、ワークロードとして [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、トレース ファイル、およびトレース テーブルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e6e60-125">The Database Engine Tuning Advisor can use [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, trace files, and trace tables as workloads.</span></span>  
  
 <span data-ttu-id="e6e60-126">XML 入力ファイルでワークロードを指定し、 **dta** ツールを使用してコマンド ラインでもワークロードを指定した場合、コマンド ラインで指定したワークロードがチューニングに使用されます。</span><span class="sxs-lookup"><span data-stu-id="e6e60-126">If you specify a workload in an XML input file and a workload on the command line with the **dta** tool, the workload specified on the command line will be used for tuning.</span></span> <span data-ttu-id="e6e60-127">コマンド ラインで指定したチューニング オプションはすべて、XML 入力ファイルで指定したオプションをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="e6e60-127">All tuning options specified on the command line override those that are specified in an XML input file.</span></span> <span data-ttu-id="e6e60-128">唯一の例外は、ユーザー定義の構成が XML 入力ファイルに評価モードで入力されている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="e6e60-128">The only exception is if a user-specified configuration is entered in the evaluate mode in the XML input file.</span></span> <span data-ttu-id="e6e60-129">たとえば、XML 入力ファイルの `Configuration` 要素に構成が入力されていて、チューニング オプションの 1 つとして `EvaluateConfiguration` 要素も指定されている場合は、XML 入力ファイルで指定されたチューニング オプションがコマンド ラインで入力されたチューニング オプションをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="e6e60-129">For example, if a configuration is entered in the `Configuration` element of the XML input file and the `EvaluateConfiguration` element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered at the command line.</span></span>  
  
 <span data-ttu-id="e6e60-130">各チューニング セッションには 1 つのワークロードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6e60-130">One workload must be specified for each tuning session.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6e60-131">例</span><span class="sxs-lookup"><span data-stu-id="e6e60-131">Example</span></span>  
 <span data-ttu-id="e6e60-132">次のコード例では、要素の**MyDatabase**トレーステーブルを指定します。 `Workload`</span><span class="sxs-lookup"><span data-stu-id="e6e60-132">The following code example specifies the **MyDatabase.MyDBOwner.TuningTable001** trace table for the `Workload` element.</span></span> <span data-ttu-id="e6e60-133">**TuningTable001** は SQL Server Profiler でチューニング テンプレートを使用し、トレース出力をテーブルとして保存することによって作成されたものです。</span><span class="sxs-lookup"><span data-stu-id="e6e60-133">The **TuningTable001** was created by using the Tuning template with SQL Server Profiler and saving the trace output as a table.</span></span>  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6e60-134">参照</span><span class="sxs-lookup"><span data-stu-id="e6e60-134">See Also</span></span>  
 [<span data-ttu-id="e6e60-135">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="e6e60-135">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
