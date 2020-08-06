---
title: 監査変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittrans.f1
helpviewer_keywords:
- environment data in packages [Integration Services]
- Audit transformation
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8e302f6dd1dc5666ae65af2eb9705a4922915c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712193"
---
# <a name="audit-transformation"></a><span data-ttu-id="34f08-102">監査変換</span><span class="sxs-lookup"><span data-stu-id="34f08-102">Audit Transformation</span></span>
  <span data-ttu-id="34f08-103">監査変換により、パッケージが実行される環境に関するデータをパッケージ内のデータ フローに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="34f08-103">The Audit transformation enables the data flow in a package to include data about the environment in which the package runs.</span></span> <span data-ttu-id="34f08-104">たとえば、パッケージ、コンピューター、および演算子の名前をデータ フローに追加できます。</span><span class="sxs-lookup"><span data-stu-id="34f08-104">For example, the name of the package, computer, and operator can be added to the data flow.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="34f08-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、この情報を提供するシステム変数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="34f08-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] includes system variables that provide this information.</span></span>  
  
## <a name="system-variables"></a><span data-ttu-id="34f08-106">システム変数</span><span class="sxs-lookup"><span data-stu-id="34f08-106">System Variables</span></span>  
 <span data-ttu-id="34f08-107">次の表では、監査変換で使用できるシステム変数について説明します。</span><span class="sxs-lookup"><span data-stu-id="34f08-107">The following table describes the system variables that the Audit transformation can use.</span></span>  
  
|<span data-ttu-id="34f08-108">システム変数</span><span class="sxs-lookup"><span data-stu-id="34f08-108">System variable</span></span>|<span data-ttu-id="34f08-109">インデックス</span><span class="sxs-lookup"><span data-stu-id="34f08-109">Index</span></span>|<span data-ttu-id="34f08-110">説明</span><span class="sxs-lookup"><span data-stu-id="34f08-110">Description</span></span>|  
|---------------------|-----------|-----------------|  
|`ExecutionInstanceGUID`|<span data-ttu-id="34f08-111">0</span><span class="sxs-lookup"><span data-stu-id="34f08-111">0</span></span>|<span data-ttu-id="34f08-112">パッケージの実行インスタンスを識別する GUID です。</span><span class="sxs-lookup"><span data-stu-id="34f08-112">The GUID that identifies the execution instance of the package.</span></span>|  
|`PackageID`|<span data-ttu-id="34f08-113">1</span><span class="sxs-lookup"><span data-stu-id="34f08-113">1</span></span>|<span data-ttu-id="34f08-114">パッケージの一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="34f08-114">The unique identifier of the package.</span></span>|  
|`PackageName`|<span data-ttu-id="34f08-115">2</span><span class="sxs-lookup"><span data-stu-id="34f08-115">2</span></span>|<span data-ttu-id="34f08-116">パッケージの名前です。</span><span class="sxs-lookup"><span data-stu-id="34f08-116">The package name.</span></span>|  
|`VersionID`|<span data-ttu-id="34f08-117">3</span><span class="sxs-lookup"><span data-stu-id="34f08-117">3</span></span>|<span data-ttu-id="34f08-118">パッケージのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="34f08-118">The version of the package.</span></span>|  
|`ExecutionStartTime`|<span data-ttu-id="34f08-119">4</span><span class="sxs-lookup"><span data-stu-id="34f08-119">4</span></span>|<span data-ttu-id="34f08-120">パッケージの実行を開始した時刻です。</span><span class="sxs-lookup"><span data-stu-id="34f08-120">The time the package started to run.</span></span>|  
|`MachineName`|<span data-ttu-id="34f08-121">5</span><span class="sxs-lookup"><span data-stu-id="34f08-121">5</span></span>|<span data-ttu-id="34f08-122">コンピューター名</span><span class="sxs-lookup"><span data-stu-id="34f08-122">The computer name.</span></span>|  
|`UserName`|<span data-ttu-id="34f08-123">6</span><span class="sxs-lookup"><span data-stu-id="34f08-123">6</span></span>|<span data-ttu-id="34f08-124">パッケージを開始した人のログイン名です。</span><span class="sxs-lookup"><span data-stu-id="34f08-124">The login name of the person who started the package.</span></span>|  
|`TaskName`|<span data-ttu-id="34f08-125">7</span><span class="sxs-lookup"><span data-stu-id="34f08-125">7</span></span>|<span data-ttu-id="34f08-126">監査変換が関連付けられているデータ フロー タスクの名前です。</span><span class="sxs-lookup"><span data-stu-id="34f08-126">The name of the Data Flow task with which the Audit transformation is associated.</span></span>|  
|<span data-ttu-id="34f08-127">**TaskId**</span><span class="sxs-lookup"><span data-stu-id="34f08-127">**TaskId**</span></span>|<span data-ttu-id="34f08-128">8</span><span class="sxs-lookup"><span data-stu-id="34f08-128">8</span></span>|<span data-ttu-id="34f08-129">データ フロー タスクの一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="34f08-129">The unique identifier of the Data Flow task.</span></span>|  
  
## <a name="configuration-of-the-audit-transformation"></a><span data-ttu-id="34f08-130">監査変換の構成</span><span class="sxs-lookup"><span data-stu-id="34f08-130">Configuration of the Audit Transformation</span></span>  
 <span data-ttu-id="34f08-131">監査変換を構成するには、新しい出力列の名前を設定し、変換出力に追加します。次に、その出力列にシステム変数をマップします。</span><span class="sxs-lookup"><span data-stu-id="34f08-131">You configure the Audit transformation by providing the name of a new output column to add to the transformation output, and then mapping the system variable to the output column.</span></span> <span data-ttu-id="34f08-132">1 つのシステム変数は、複数の列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="34f08-132">You can map a single system variable to multiple columns.</span></span>  
  
 <span data-ttu-id="34f08-133">この変換は 1 つの入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="34f08-133">This transformation has one input and one output.</span></span> <span data-ttu-id="34f08-134">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="34f08-134">It does not support an error output.</span></span>  
  
 <span data-ttu-id="34f08-135">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="34f08-135">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="34f08-136">**[監査変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [Audit Transformation Editor](../../audit-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34f08-136">For more information about the properties that you can set in the **Audit Transformation Editor** dialog box, see [Audit Transformation Editor](../../audit-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="34f08-137">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="34f08-137">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="34f08-138">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="34f08-138">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="34f08-139">Common Properties</span><span class="sxs-lookup"><span data-stu-id="34f08-139">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="34f08-140">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="34f08-140">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="34f08-141">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34f08-141">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
