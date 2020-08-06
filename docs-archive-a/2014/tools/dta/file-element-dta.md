---
title: File 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0eeb2bdcc9513ca6283447daca63c8bbc4fa1726
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720661"
---
# <a name="file-element-dta"></a><span data-ttu-id="0a82b-102">File 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="0a82b-102">File Element (DTA)</span></span>
  <span data-ttu-id="0a82b-103">ワークロード ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a82b-103">Specifies the workload file.</span></span> <span data-ttu-id="0a82b-104">ワークロードとは、チューニングするデータベースに対して実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのセットです。</span><span class="sxs-lookup"><span data-stu-id="0a82b-104">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="0a82b-105">ワークロード ファイルには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト (.sql) またはトレース ファイル (.trc) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0a82b-105">Workload files can be [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts (.sql) or trace files (.trc).</span></span> <span data-ttu-id="0a82b-106">詳細については、「 [データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a82b-106">For more information, see [Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a82b-107">構文</span><span class="sxs-lookup"><span data-stu-id="0a82b-107">Syntax</span></span>  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="0a82b-108">要素の特性</span><span class="sxs-lookup"><span data-stu-id="0a82b-108">Element Characteristics</span></span>  
  
|<span data-ttu-id="0a82b-109">特徴</span><span class="sxs-lookup"><span data-stu-id="0a82b-109">Characteristic</span></span>|<span data-ttu-id="0a82b-110">説明</span><span class="sxs-lookup"><span data-stu-id="0a82b-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0a82b-111">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="0a82b-111">**Data type and length**</span></span>|<span data-ttu-id="0a82b-112">`string` データ型を使用して、ワークロード ファイルのあるディレクトリへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a82b-112">Use the `string` data type to specify the directory path to your workload file.</span></span> <span data-ttu-id="0a82b-113">例:</span><span class="sxs-lookup"><span data-stu-id="0a82b-113">For example:</span></span><br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> <span data-ttu-id="0a82b-114">長さの制限は、サーバーによって決まります。</span><span class="sxs-lookup"><span data-stu-id="0a82b-114">Length limit is enforced by the server.</span></span>|  
|<span data-ttu-id="0a82b-115">**既定値**</span><span class="sxs-lookup"><span data-stu-id="0a82b-115">**Default value**</span></span>|<span data-ttu-id="0a82b-116">[なし] :</span><span class="sxs-lookup"><span data-stu-id="0a82b-116">None.</span></span>|  
|<span data-ttu-id="0a82b-117">**個数**</span><span class="sxs-lookup"><span data-stu-id="0a82b-117">**Occurrence**</span></span>|<span data-ttu-id="0a82b-118">他の種類のワークロードが指定されていない場合は、1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="0a82b-118">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="0a82b-119">**EventString**親要素に対しては、 **File**、 **Database** 、または **Workload** 子要素を指定する必要がありますが、使用できるのは 1 種類だけです。</span><span class="sxs-lookup"><span data-stu-id="0a82b-119">You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used.</span></span> <span data-ttu-id="0a82b-120">たとえば、 **File** 要素を使用してワークロードを指定した場合は、同じ XML 入力ファイル内で **Database** 要素を使用してワークロードを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="0a82b-120">For example, if you specify a workload with the **File** element, then you cannot also specify a workload with the **Database** element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="0a82b-121">要素の関係</span><span class="sxs-lookup"><span data-stu-id="0a82b-121">Element Relationships</span></span>  
  
|<span data-ttu-id="0a82b-122">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="0a82b-122">Relationship</span></span>|<span data-ttu-id="0a82b-123">要素</span><span class="sxs-lookup"><span data-stu-id="0a82b-123">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="0a82b-124">**親要素**</span><span class="sxs-lookup"><span data-stu-id="0a82b-124">**Parent element**</span></span>|[<span data-ttu-id="0a82b-125">Workload 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="0a82b-125">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="0a82b-126">**子要素**</span><span class="sxs-lookup"><span data-stu-id="0a82b-126">**Child elements**</span></span>|<span data-ttu-id="0a82b-127">[なし] :</span><span class="sxs-lookup"><span data-stu-id="0a82b-127">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0a82b-128">例</span><span class="sxs-lookup"><span data-stu-id="0a82b-128">Example</span></span>  
 <span data-ttu-id="0a82b-129">この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a82b-129">For a usage example of this element, see [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a82b-130">参照</span><span class="sxs-lookup"><span data-stu-id="0a82b-130">See Also</span></span>  
 [<span data-ttu-id="0a82b-131">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="0a82b-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
