---
title: 監査変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af6490643a0bef60cca961dc9a0564c5f6b46484
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740242"
---
# <a name="audit-transformation-editor"></a><span data-ttu-id="6ade7-102">監査変換エディター</span><span class="sxs-lookup"><span data-stu-id="6ade7-102">Audit Transformation Editor</span></span>
  <span data-ttu-id="6ade7-103">監査変換により、パッケージが実行される環境に関するデータをパッケージ内のデータ フローに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6ade7-103">The Audit transformation enables the data flow in a package to include data about the environment in which the package runs.</span></span> <span data-ttu-id="6ade7-104">たとえば、パッケージ、コンピューター、および演算子の名前をデータ フローに追加できます。</span><span class="sxs-lookup"><span data-stu-id="6ade7-104">For example, the name of the package, computer, and operator can be added to the data flow.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6ade7-105">には、この情報を提供するシステム変数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ade7-105">includes system variables that provide this information.</span></span>  
  
 <span data-ttu-id="6ade7-106">監査変換の詳細については、「 [Audit Transformation](data-flow/transformations/audit-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ade7-106">To learn more about the Audit transformation, see [Audit Transformation](data-flow/transformations/audit-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6ade7-107">Options</span><span class="sxs-lookup"><span data-stu-id="6ade7-107">Options</span></span>  
 <span data-ttu-id="6ade7-108">**出力列の名前**</span><span class="sxs-lookup"><span data-stu-id="6ade7-108">**Output column name**</span></span>  
 <span data-ttu-id="6ade7-109">監査情報を格納する、新しい出力列の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-109">Provide the name for a new output column that will contain the audit information.</span></span>  
  
 <span data-ttu-id="6ade7-110">**[監査の種類]**</span><span class="sxs-lookup"><span data-stu-id="6ade7-110">**Audit type**</span></span>  
 <span data-ttu-id="6ade7-111">監査情報を得るために使用できるシステム変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-111">Select an available system variable to supply the audit information.</span></span>  
  
|<span data-ttu-id="6ade7-112">値</span><span class="sxs-lookup"><span data-stu-id="6ade7-112">Value</span></span>|<span data-ttu-id="6ade7-113">[説明]</span><span class="sxs-lookup"><span data-stu-id="6ade7-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6ade7-114">**[実行インスタンスの GUID]**</span><span class="sxs-lookup"><span data-stu-id="6ade7-114">**Execution instance GUID**</span></span>|<span data-ttu-id="6ade7-115">パッケージの実行インスタンスを個別に識別する GUID を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-115">Insert the GUID that uniquely identifies the execution instance of the package.</span></span>|  
|<span data-ttu-id="6ade7-116">**[パッケージ ID]**</span><span class="sxs-lookup"><span data-stu-id="6ade7-116">**Package ID**</span></span>|<span data-ttu-id="6ade7-117">パッケージを個別に識別する GUID を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-117">Insert the GUID that uniquely identifies the package.</span></span>|  
|<span data-ttu-id="6ade7-118">**パッケージ名**</span><span class="sxs-lookup"><span data-stu-id="6ade7-118">**Package name**</span></span>|<span data-ttu-id="6ade7-119">パッケージ名を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-119">Insert the package name.</span></span>|  
|<span data-ttu-id="6ade7-120">**バージョン ID**</span><span class="sxs-lookup"><span data-stu-id="6ade7-120">**Version ID**</span></span>|<span data-ttu-id="6ade7-121">パッケージのバージョンを個別に識別する GUID を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-121">Insert the GUID that uniquely identifies the version of the package.</span></span>|  
|<span data-ttu-id="6ade7-122">**[実行開始時刻]**</span><span class="sxs-lookup"><span data-stu-id="6ade7-122">**Execution start time**</span></span>|<span data-ttu-id="6ade7-123">パッケージの実行が開始される時刻を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-123">Insert the time at which package execution started.</span></span>|  
|<span data-ttu-id="6ade7-124">**コンピューター名**</span><span class="sxs-lookup"><span data-stu-id="6ade7-124">**Machine name**</span></span>|<span data-ttu-id="6ade7-125">パッケージを起動したコンピューターの名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-125">Insert the name of the computer on which the package was launched.</span></span>|  
|<span data-ttu-id="6ade7-126">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="6ade7-126">**User name**</span></span>|<span data-ttu-id="6ade7-127">パッケージを起動したユーザーのログイン名を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-127">Insert the login name of the user who launched the package.</span></span>|  
|<span data-ttu-id="6ade7-128">**タスク名**</span><span class="sxs-lookup"><span data-stu-id="6ade7-128">**Task name**</span></span>|<span data-ttu-id="6ade7-129">監査変換が関連付けられているデータ フロー タスクの名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-129">Insert the name of the Data Flow task with which the Audit transformation is associated.</span></span>|  
|<span data-ttu-id="6ade7-130">**タスク ID**</span><span class="sxs-lookup"><span data-stu-id="6ade7-130">**Task ID**</span></span>|<span data-ttu-id="6ade7-131">監査変換が関連付けられているデータ フロー タスクを個別に識別する GUID を挿入します。</span><span class="sxs-lookup"><span data-stu-id="6ade7-131">Insert the GUID that uniquely identifies the Data Flow task with which the Audit transformation is associated.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ade7-132">参照</span><span class="sxs-lookup"><span data-stu-id="6ade7-132">See Also</span></span>  
 [<span data-ttu-id="6ade7-133">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="6ade7-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
