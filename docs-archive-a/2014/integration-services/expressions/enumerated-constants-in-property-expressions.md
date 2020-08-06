---
title: プロパティ式における列挙定数 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9cb4ae32bf564e98d8cfc843e9497b15222fa79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716542"
---
# <a name="enumerated-constants-in-property-expressions"></a><span data-ttu-id="bc0ae-102">プロパティ式における列挙定数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-102">Enumerated Constants in Property Expressions</span></span>
  <span data-ttu-id="bc0ae-103">プロパティ式に列挙子メンバー リストの値が含まれている場合、この式ではメンバーの表示名ではなく、列挙子メンバーの数値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-103">If property expressions include values from an enumerator member list, the expression must use the numeric value of the enumerator member instead of the friendly name of the member.</span></span> <span data-ttu-id="bc0ae-104">たとえば、式で `LoggingMode` プロパティを設定する場合、表示名 Disabled ではなく、数値 2 を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-104">For example, if an expression sets the `LoggingMode` property then you must use the numeric value 2 instead of the friendly name Disabled.</span></span>  
  
 <span data-ttu-id="bc0ae-105">このトピックでは、プロパティ式でメンバーがよく使用される列挙子の表示名に対応した数値のみを示します。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-105">This topic lists only the numeric values equivalent to friendly names of enumerators whose members are commonly used in property expressions.</span></span> <span data-ttu-id="bc0ae-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルには、パッケージをプログラムで構築したり、タスクやデータ フロー コンポーネントなどのカスタム パッケージ要素をコード化する際に使用する列挙子が多数追加されています。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-106">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model includes many additional enumerators that you use when you program the object model to build packages programmatically or code custom package elements such as tasks and data flow components.</span></span>  
  
 <span data-ttu-id="bc0ae-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のプロパティ ウィンドウには、パッケージとパッケージ オブジェクトのカスタム プロパティに加えて、パッケージ、タスク、Foreach ループ コンテナー、For ループ コンテナー、およびシーケンス コンテナーで使用できる一連のプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-107">In addition to the custom properties for packages and package objects, the Properties window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] includes a set of properties that are available to packages, tasks, and the Foreach Loop, For Loop, and Sequence containers.</span></span> <span data-ttu-id="bc0ae-108">列挙子からの値によって設定される共通プロパティである、、 `ForceExecutionResult` `LoggingMode` `IsolationLevel` 、、およびは、[ `Transaction Option` 共通プロパティ] セクションに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-108">The common properties that are set by values from enumerators-`ForceExecutionResult`, `LoggingMode`, `IsolationLevel`, and `Transaction Option`-are listed in Common Properties section.</span></span>  
  
 <span data-ttu-id="bc0ae-109">次の各セクションでは、列挙定数について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-109">The following sections provide information about enumerated constants:</span></span>  
  
 [<span data-ttu-id="bc0ae-110">Package</span><span class="sxs-lookup"><span data-stu-id="bc0ae-110">Package</span></span>](#Package)  
  
 [<span data-ttu-id="bc0ae-111">Foreach ループ列挙子</span><span class="sxs-lookup"><span data-stu-id="bc0ae-111">Foreach Loop Enumerators</span></span>](#Foreach)  
  
 [<span data-ttu-id="bc0ae-112">タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-112">Tasks</span></span>](#Tasks)  
  
 [<span data-ttu-id="bc0ae-113">メンテナンス プランのタスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-113">Maintenance Plan Tasks</span></span>](#MaintenancePlanTasks)  
  
 [<span data-ttu-id="bc0ae-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="bc0ae-114">Common Properties</span></span>](#CommonProperties)  
  
##  <a name="package"></a><a name="Package"></a> <span data-ttu-id="bc0ae-115">[パッケージ]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-115">Package</span></span>  
 <span data-ttu-id="bc0ae-116">次の表は、列挙子からの値を使用して設定する、パッケージのプロパティの表示名とそれに対応する数値を示します。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-116">The following tables lists the friendly names and the numeric value equivalents for properties of packages that you set by using values from an enumerator.</span></span>  
  
 <span data-ttu-id="bc0ae-117">`PackageType`列挙体の値を使用してプロパティを設定し `DTSPackageType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-117">`PackageType` property-Set by using values from the `DTSPackageType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-118">DTSPackageType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-118">Friendly name in DTSPackageType</span></span>|<span data-ttu-id="bc0ae-119">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-119">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-120">Default</span><span class="sxs-lookup"><span data-stu-id="bc0ae-120">Default</span></span>|<span data-ttu-id="bc0ae-121">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-121">0</span></span>|  
|<span data-ttu-id="bc0ae-122">DTSWizard</span><span class="sxs-lookup"><span data-stu-id="bc0ae-122">DTSWizard</span></span>|<span data-ttu-id="bc0ae-123">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-123">1</span></span>|  
|<span data-ttu-id="bc0ae-124">DTSDesigner</span><span class="sxs-lookup"><span data-stu-id="bc0ae-124">DTSDesigner</span></span>|<span data-ttu-id="bc0ae-125">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-125">2</span></span>|  
|<span data-ttu-id="bc0ae-126">SQLReplication</span><span class="sxs-lookup"><span data-stu-id="bc0ae-126">SQLReplication</span></span>|<span data-ttu-id="bc0ae-127">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-127">3</span></span>|  
|<span data-ttu-id="bc0ae-128">DTSDesigner100</span><span class="sxs-lookup"><span data-stu-id="bc0ae-128">DTSDesigner100</span></span>|<span data-ttu-id="bc0ae-129">5</span><span class="sxs-lookup"><span data-stu-id="bc0ae-129">5</span></span>|  
|<span data-ttu-id="bc0ae-130">SQLDBMaint</span><span class="sxs-lookup"><span data-stu-id="bc0ae-130">SQLDBMaint</span></span>|<span data-ttu-id="bc0ae-131">6</span><span class="sxs-lookup"><span data-stu-id="bc0ae-131">6</span></span>|  
  
 <span data-ttu-id="bc0ae-132">`CheckpointUsage`列挙体の値を使用してプロパティを設定し `DTSCheckpointUsage` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-132">`CheckpointUsage` property-Set by using values from the `DTSCheckpointUsage` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-133">DTSCheckpointUsage の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-133">Friendly name in DTSCheckpointUsage</span></span>|<span data-ttu-id="bc0ae-134">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-134">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-135">なし</span><span class="sxs-lookup"><span data-stu-id="bc0ae-135">Never</span></span>|<span data-ttu-id="bc0ae-136">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-136">0</span></span>|  
|<span data-ttu-id="bc0ae-137">IfExists</span><span class="sxs-lookup"><span data-stu-id="bc0ae-137">IfExists</span></span>|<span data-ttu-id="bc0ae-138">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-138">1</span></span>|  
|<span data-ttu-id="bc0ae-139">Always (常に)</span><span class="sxs-lookup"><span data-stu-id="bc0ae-139">Always</span></span>|<span data-ttu-id="bc0ae-140">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-140">2</span></span>|  
  
 <span data-ttu-id="bc0ae-141">`PackagePriorityClass`列挙体の値を使用してプロパティを設定し `DTSPriorityClass` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-141">`PackagePriorityClass` property-Set by using values from the `DTSPriorityClass` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-142">DTSPriorityClass の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-142">Friendly name in DTSPriorityClass</span></span>|<span data-ttu-id="bc0ae-143">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-143">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-144">Default</span><span class="sxs-lookup"><span data-stu-id="bc0ae-144">Default</span></span>|<span data-ttu-id="bc0ae-145">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-145">0</span></span>|  
|<span data-ttu-id="bc0ae-146">AboveNormal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-146">AboveNormal</span></span>|<span data-ttu-id="bc0ae-147">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-147">1</span></span>|  
|<span data-ttu-id="bc0ae-148">Normal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-148">Normal</span></span>|<span data-ttu-id="bc0ae-149">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-149">2</span></span>|  
|<span data-ttu-id="bc0ae-150">BelowNormal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-150">BelowNormal</span></span>|<span data-ttu-id="bc0ae-151">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-151">3</span></span>|  
|<span data-ttu-id="bc0ae-152">アイドル</span><span class="sxs-lookup"><span data-stu-id="bc0ae-152">Idle</span></span>|<span data-ttu-id="bc0ae-153">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-153">4</span></span>|  
  
 <span data-ttu-id="bc0ae-154">`ProtectionLevel`列挙体の値を使用してプロパティを設定し `DTSProtectionLevel` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-154">`ProtectionLevel` property-Set by using values from the `DTSProtectionLevel` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-155">DTSProtectionLevel の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-155">Friendly name in DTSProtectionLevel</span></span>|<span data-ttu-id="bc0ae-156">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-156">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-157">DontSaveSensitive</span><span class="sxs-lookup"><span data-stu-id="bc0ae-157">DontSaveSensitive</span></span>|<span data-ttu-id="bc0ae-158">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-158">0</span></span>|  
|<span data-ttu-id="bc0ae-159">EncryptSensitiveWithUserKey</span><span class="sxs-lookup"><span data-stu-id="bc0ae-159">EncryptSensitiveWithUserKey</span></span>|<span data-ttu-id="bc0ae-160">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-160">1</span></span>|  
|<span data-ttu-id="bc0ae-161">EncryptSensitiveWithPassword</span><span class="sxs-lookup"><span data-stu-id="bc0ae-161">EncryptSensitiveWithPassword</span></span>|<span data-ttu-id="bc0ae-162">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-162">2</span></span>|  
|<span data-ttu-id="bc0ae-163">EncryptAllWithPassword</span><span class="sxs-lookup"><span data-stu-id="bc0ae-163">EncryptAllWithPassword</span></span>|<span data-ttu-id="bc0ae-164">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-164">3</span></span>|  
|<span data-ttu-id="bc0ae-165">EncryptAllWithUserKey</span><span class="sxs-lookup"><span data-stu-id="bc0ae-165">EncryptAllWithUserKey</span></span>|<span data-ttu-id="bc0ae-166">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-166">4</span></span>|  
|<span data-ttu-id="bc0ae-167">ServerStorage</span><span class="sxs-lookup"><span data-stu-id="bc0ae-167">ServerStorage</span></span>|<span data-ttu-id="bc0ae-168">5</span><span class="sxs-lookup"><span data-stu-id="bc0ae-168">5</span></span>|  
  
##  <a name="precedence-constraints"></a><a name="PrecedenceConstraints"></a> <span data-ttu-id="bc0ae-169">優先順位制約</span><span class="sxs-lookup"><span data-stu-id="bc0ae-169">Precedence Constraints</span></span>  
 <span data-ttu-id="bc0ae-170">`EvalOp`列挙体の値を使用してプロパティを設定し `DTSPrecedenceEvalOp` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-170">`EvalOp` property-Set by using values from the `DTSPrecedenceEvalOp` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-171">DTSPrecedenceEvalOp の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-171">Friendly name in DTSPrecedenceEvalOp</span></span>|<span data-ttu-id="bc0ae-172">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-172">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-173">式</span><span class="sxs-lookup"><span data-stu-id="bc0ae-173">Expression</span></span>|<span data-ttu-id="bc0ae-174">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-174">1</span></span>|  
|<span data-ttu-id="bc0ae-175">制約</span><span class="sxs-lookup"><span data-stu-id="bc0ae-175">Constraint</span></span>|<span data-ttu-id="bc0ae-176">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-176">2</span></span>|  
|<span data-ttu-id="bc0ae-177">ExpressionAndConstraint</span><span class="sxs-lookup"><span data-stu-id="bc0ae-177">ExpressionAndConstraint</span></span>|<span data-ttu-id="bc0ae-178">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-178">3</span></span>|  
|<span data-ttu-id="bc0ae-179">ExpressionOrConstraint</span><span class="sxs-lookup"><span data-stu-id="bc0ae-179">ExpressionOrConstraint</span></span>|<span data-ttu-id="bc0ae-180">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-180">4</span></span>|  
  
 <span data-ttu-id="bc0ae-181">`Value`列挙体の値を使用してプロパティを設定し `DTSExecResult` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-181">`Value` property-Set by using values from the `DTSExecResult` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-182">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-182">Friendly Name</span></span>|<span data-ttu-id="bc0ae-183">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-183">Numeric Value</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="bc0ae-184">Success</span><span class="sxs-lookup"><span data-stu-id="bc0ae-184">Success</span></span>|<span data-ttu-id="bc0ae-185">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-185">0</span></span>|  
|<span data-ttu-id="bc0ae-186">障害</span><span class="sxs-lookup"><span data-stu-id="bc0ae-186">Failure</span></span>|<span data-ttu-id="bc0ae-187">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-187">1</span></span>|  
|<span data-ttu-id="bc0ae-188">Completion</span><span class="sxs-lookup"><span data-stu-id="bc0ae-188">Completion</span></span>|<span data-ttu-id="bc0ae-189">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-189">2</span></span>|  
|<span data-ttu-id="bc0ae-190">Canceled</span><span class="sxs-lookup"><span data-stu-id="bc0ae-190">Canceled</span></span>|<span data-ttu-id="bc0ae-191">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-191">3</span></span>|  
  
##  <a name="foreach-loop-enumerators"></a><a name="Foreach"></a> <span data-ttu-id="bc0ae-192">Foreach ループ列挙子</span><span class="sxs-lookup"><span data-stu-id="bc0ae-192">Foreach Loop Enumerators</span></span>  
 <span data-ttu-id="bc0ae-193">Foreach ループには、プロパティ式で設定できるプロパティを含む一連の列挙子があります。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-193">The Foreach Loop includes a set of enumerators with properties that can be set by property expressions.</span></span>  
  
### <a name="foreach-ado-enumerator"></a><span data-ttu-id="bc0ae-194">Foreach ADO 列挙子</span><span class="sxs-lookup"><span data-stu-id="bc0ae-194">Foreach ADO Enumerator</span></span>  
 <span data-ttu-id="bc0ae-195">`Type`列挙体の値を使用してプロパティを設定し `ADOEnumerationType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-195">`Type` property-Set by using values from the `ADOEnumerationType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-196">ADOEnumerationType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-196">Friendly name in ADOEnumerationType</span></span>|<span data-ttu-id="bc0ae-197">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-197">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-198">EnumerateTables</span><span class="sxs-lookup"><span data-stu-id="bc0ae-198">EnumerateTables</span></span>|<span data-ttu-id="bc0ae-199">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-199">0</span></span>|  
|<span data-ttu-id="bc0ae-200">EnumerateAllRows</span><span class="sxs-lookup"><span data-stu-id="bc0ae-200">EnumerateAllRows</span></span>|<span data-ttu-id="bc0ae-201">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-201">1</span></span>|  
|<span data-ttu-id="bc0ae-202">EnumerateRowsInFirstTable</span><span class="sxs-lookup"><span data-stu-id="bc0ae-202">EnumerateRowsInFirstTable</span></span>|<span data-ttu-id="bc0ae-203">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-203">2</span></span>|  
  
### <a name="foreach-nodelist-enumerator"></a><span data-ttu-id="bc0ae-204">Foreach Nodelist 列挙子</span><span class="sxs-lookup"><span data-stu-id="bc0ae-204">Foreach Nodelist Enumerator</span></span>  
 <span data-ttu-id="bc0ae-205">`SourceDocumentType`、 `InnerXPathStringSourceType` 、および **[outerxpathstringsourcetype]** の各プロパティ-列挙の値を使用して設定さ `SourceType` れます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-205">`SourceDocumentType`, `InnerXPathStringSourceType`, and **OuterXPathStringSourceType** properties-Set by using values from the `SourceType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-206">SourceType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-206">Friendly name in SourceType</span></span>|<span data-ttu-id="bc0ae-207">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-207">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-208">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-208">FileConnection</span></span>|<span data-ttu-id="bc0ae-209">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-209">0</span></span>|  
|<span data-ttu-id="bc0ae-210">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-210">Variable</span></span>|<span data-ttu-id="bc0ae-211">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-211">1</span></span>|  
|<span data-ttu-id="bc0ae-212">DirectInput</span><span class="sxs-lookup"><span data-stu-id="bc0ae-212">DirectInput</span></span>|<span data-ttu-id="bc0ae-213">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-213">2</span></span>|  
  
 <span data-ttu-id="bc0ae-214">`EnumerationType`列挙体の値を使用してプロパティを設定し `EnumerationType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-214">`EnumerationType` property-Set by using values from the `EnumerationType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-215">EnumerationType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-215">Friendly name in EnumerationType</span></span>|<span data-ttu-id="bc0ae-216">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-216">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-217">ナビゲーター</span><span class="sxs-lookup"><span data-stu-id="bc0ae-217">Navigator</span></span>|<span data-ttu-id="bc0ae-218">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-218">0</span></span>|  
|<span data-ttu-id="bc0ae-219">ノード</span><span class="sxs-lookup"><span data-stu-id="bc0ae-219">Node</span></span>|<span data-ttu-id="bc0ae-220">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-220">1</span></span>|  
|<span data-ttu-id="bc0ae-221">NodeText</span><span class="sxs-lookup"><span data-stu-id="bc0ae-221">NodeText</span></span>|<span data-ttu-id="bc0ae-222">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-222">2</span></span>|  
|<span data-ttu-id="bc0ae-223">ElementCollection</span><span class="sxs-lookup"><span data-stu-id="bc0ae-223">ElementCollection</span></span>|<span data-ttu-id="bc0ae-224">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-224">3</span></span>|  
  
 <span data-ttu-id="bc0ae-225">`InnerElementType`列挙体の値を使用してプロパティを設定し `InnerElementType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-225">`InnerElementType` property-Set by using values from the `InnerElementType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-226">InnerElementType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-226">Friendly name in InnerElementType</span></span>|<span data-ttu-id="bc0ae-227">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-227">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-228">ナビゲーター</span><span class="sxs-lookup"><span data-stu-id="bc0ae-228">Navigator</span></span>|<span data-ttu-id="bc0ae-229">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-229">0</span></span>|  
|<span data-ttu-id="bc0ae-230">ノード</span><span class="sxs-lookup"><span data-stu-id="bc0ae-230">Node</span></span>|<span data-ttu-id="bc0ae-231">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-231">1</span></span>|  
|<span data-ttu-id="bc0ae-232">NodeText</span><span class="sxs-lookup"><span data-stu-id="bc0ae-232">NodeText</span></span>|<span data-ttu-id="bc0ae-233">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-233">2</span></span>|  
  
##  <a name="tasks"></a><a name="Tasks"></a> <span data-ttu-id="bc0ae-234">処理手順</span><span class="sxs-lookup"><span data-stu-id="bc0ae-234">Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="bc0ae-235">には、プロパティ式で設定できるプロパティを含む多くのタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-235">includes numerous tasks with properties that can be set by property expressions.</span></span>  
  
### <a name="analysis-services-execute-ddl-task"></a><span data-ttu-id="bc0ae-236">Analysis Services DDL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-236">Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="bc0ae-237">`SourceType`列挙体の値を使用してプロパティを設定し `DDLSourceType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-237">`SourceType` property-Set by using values from the `DDLSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-238">DDLSourceType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-238">Friendly name in DDLSourceType</span></span>|<span data-ttu-id="bc0ae-239">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-239">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-240">DirectInput</span><span class="sxs-lookup"><span data-stu-id="bc0ae-240">DirectInput</span></span>|<span data-ttu-id="bc0ae-241">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-241">0</span></span>|  
|<span data-ttu-id="bc0ae-242">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-242">FileConnection</span></span>|<span data-ttu-id="bc0ae-243">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-243">1</span></span>|  
|<span data-ttu-id="bc0ae-244">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-244">Variable</span></span>|<span data-ttu-id="bc0ae-245">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-245">2</span></span>|  
  
### <a name="bulk-insert-task"></a><span data-ttu-id="bc0ae-246">一括挿入タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-246">Bulk Insert Task</span></span>  
 <span data-ttu-id="bc0ae-247">`DataFileType`列挙体の値を使用してプロパティを設定し `DTSBulkInsert_DataFileType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-247">`DataFileType` property-Set by using values from the `DTSBulkInsert_DataFileType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-248">DTSBulkInsert_DataFileType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-248">Friendly name in DTSBulkInsert_DataFileType</span></span>|<span data-ttu-id="bc0ae-249">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-249">Numeric value</span></span>|  
|--------------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-250">DTSBulkInsert_DataFileType_Char</span><span class="sxs-lookup"><span data-stu-id="bc0ae-250">DTSBulkInsert_DataFileType_Char</span></span>|<span data-ttu-id="bc0ae-251">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-251">0</span></span>|  
|<span data-ttu-id="bc0ae-252">DTSBulkInsert_DataFileType_Native</span><span class="sxs-lookup"><span data-stu-id="bc0ae-252">DTSBulkInsert_DataFileType_Native</span></span>|<span data-ttu-id="bc0ae-253">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-253">1</span></span>|  
|<span data-ttu-id="bc0ae-254">DTSBulkInsert_DataFileType_WideChar</span><span class="sxs-lookup"><span data-stu-id="bc0ae-254">DTSBulkInsert_DataFileType_WideChar</span></span>|<span data-ttu-id="bc0ae-255">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-255">2</span></span>|  
|<span data-ttu-id="bc0ae-256">DTSBulkInsert_DataFileType_WideNative</span><span class="sxs-lookup"><span data-stu-id="bc0ae-256">DTSBulkInsert_DataFileType_WideNative</span></span>|<span data-ttu-id="bc0ae-257">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-257">3</span></span>|  
  
### <a name="execute-sql-task"></a><span data-ttu-id="bc0ae-258">SQL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-258">Execute SQL Task</span></span>  
 <span data-ttu-id="bc0ae-259">`ResultSetType`列挙体の値を使用してプロパティを設定し `ResultSetType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-259">`ResultSetType` property-Set by using values from the `ResultSetType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-260">ResultSetType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-260">Friendly name in ResultSetType</span></span>|<span data-ttu-id="bc0ae-261">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-261">Numeric Value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-262">ResultSetType_None</span><span class="sxs-lookup"><span data-stu-id="bc0ae-262">ResultSetType_None</span></span>|<span data-ttu-id="bc0ae-263">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-263">1</span></span>|  
|<span data-ttu-id="bc0ae-264">ResultSetType_SingleRow</span><span class="sxs-lookup"><span data-stu-id="bc0ae-264">ResultSetType_SingleRow</span></span>|<span data-ttu-id="bc0ae-265">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-265">2</span></span>|  
|<span data-ttu-id="bc0ae-266">ResultSetType_Rowset</span><span class="sxs-lookup"><span data-stu-id="bc0ae-266">ResultSetType_Rowset</span></span>|<span data-ttu-id="bc0ae-267">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-267">3</span></span>|  
|<span data-ttu-id="bc0ae-268">ResultSetType_XML</span><span class="sxs-lookup"><span data-stu-id="bc0ae-268">ResultSetType_XML</span></span>|<span data-ttu-id="bc0ae-269">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-269">4</span></span>|  
  
 <span data-ttu-id="bc0ae-270">`SqlStatementSourceType`列挙体の値を使用してプロパティを設定し `SqlStatementSourceType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-270">`SqlStatementSourceType` property-Set by using values from the `SqlStatementSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-271">SqlStatementSourceType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-271">Friendly name in SqlStatementSourceType</span></span>|<span data-ttu-id="bc0ae-272">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-272">Numeric Value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-273">DirectInput</span><span class="sxs-lookup"><span data-stu-id="bc0ae-273">DirectInput</span></span>|<span data-ttu-id="bc0ae-274">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-274">1</span></span>|  
|<span data-ttu-id="bc0ae-275">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-275">FileConnection</span></span>|<span data-ttu-id="bc0ae-276">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-276">2</span></span>|  
|<span data-ttu-id="bc0ae-277">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-277">Variable</span></span>|<span data-ttu-id="bc0ae-278">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-278">3</span></span>|  
  
### <a name="file-system-task"></a><span data-ttu-id="bc0ae-279">ファイル システム タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-279">File System Task</span></span>  
 <span data-ttu-id="bc0ae-280">`Operation`列挙体の値を使用してプロパティを設定し `DTSFileSystemOperation` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-280">`Operation` property-Set by using values from the `DTSFileSystemOperation` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-281">DTSFileSystemOperation の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-281">Friendly name in DTSFileSystemOperation</span></span>|<span data-ttu-id="bc0ae-282">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-282">Numeric value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-283">CopyFile</span><span class="sxs-lookup"><span data-stu-id="bc0ae-283">CopyFile</span></span>|<span data-ttu-id="bc0ae-284">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-284">0</span></span>|  
|<span data-ttu-id="bc0ae-285">MoveFile</span><span class="sxs-lookup"><span data-stu-id="bc0ae-285">MoveFile</span></span>|<span data-ttu-id="bc0ae-286">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-286">1</span></span>|  
|<span data-ttu-id="bc0ae-287">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="bc0ae-287">DeleteFile</span></span>|<span data-ttu-id="bc0ae-288">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-288">2</span></span>|  
|<span data-ttu-id="bc0ae-289">RenameFile</span><span class="sxs-lookup"><span data-stu-id="bc0ae-289">RenameFile</span></span>|<span data-ttu-id="bc0ae-290">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-290">3</span></span>|  
|<span data-ttu-id="bc0ae-291">SetAttributes</span><span class="sxs-lookup"><span data-stu-id="bc0ae-291">SetAttributes</span></span>|<span data-ttu-id="bc0ae-292">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-292">4</span></span>|  
|<span data-ttu-id="bc0ae-293">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="bc0ae-293">CreateDirectory</span></span>|<span data-ttu-id="bc0ae-294">5</span><span class="sxs-lookup"><span data-stu-id="bc0ae-294">5</span></span>|  
|<span data-ttu-id="bc0ae-295">CopyDirectory</span><span class="sxs-lookup"><span data-stu-id="bc0ae-295">CopyDirectory</span></span>|<span data-ttu-id="bc0ae-296">6</span><span class="sxs-lookup"><span data-stu-id="bc0ae-296">6</span></span>|  
|<span data-ttu-id="bc0ae-297">MoveDirectory</span><span class="sxs-lookup"><span data-stu-id="bc0ae-297">MoveDirectory</span></span>|<span data-ttu-id="bc0ae-298">7</span><span class="sxs-lookup"><span data-stu-id="bc0ae-298">7</span></span>|  
|<span data-ttu-id="bc0ae-299">DeleteDirectory</span><span class="sxs-lookup"><span data-stu-id="bc0ae-299">DeleteDirectory</span></span>|<span data-ttu-id="bc0ae-300">8</span><span class="sxs-lookup"><span data-stu-id="bc0ae-300">8</span></span>|  
|<span data-ttu-id="bc0ae-301">DeleteDirectoryContent</span><span class="sxs-lookup"><span data-stu-id="bc0ae-301">DeleteDirectoryContent</span></span>|<span data-ttu-id="bc0ae-302">9</span><span class="sxs-lookup"><span data-stu-id="bc0ae-302">9</span></span>|  
  
 <span data-ttu-id="bc0ae-303">`Attributes`列挙体の値を使用してプロパティを設定し `DTSFileSystemAttributes` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-303">`Attributes` property-Set by using values from the `DTSFileSystemAttributes` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-304">DTSFileSystemAttributes の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-304">Friendly name in DTSFileSystemAttributes</span></span>|<span data-ttu-id="bc0ae-305">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-305">Numeric value</span></span>|  
|----------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-306">Normal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-306">Normal</span></span>|<span data-ttu-id="bc0ae-307">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-307">0</span></span>|  
|<span data-ttu-id="bc0ae-308">アーカイブ</span><span class="sxs-lookup"><span data-stu-id="bc0ae-308">Archive</span></span>|<span data-ttu-id="bc0ae-309">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-309">1</span></span>|  
|<span data-ttu-id="bc0ae-310">[非表示]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-310">Hidden</span></span>|<span data-ttu-id="bc0ae-311">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-311">2</span></span>|  
|<span data-ttu-id="bc0ae-312">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="bc0ae-312">ReadOnly</span></span>|<span data-ttu-id="bc0ae-313">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-313">4</span></span>|  
|<span data-ttu-id="bc0ae-314">システム</span><span class="sxs-lookup"><span data-stu-id="bc0ae-314">System</span></span>|<span data-ttu-id="bc0ae-315">8</span><span class="sxs-lookup"><span data-stu-id="bc0ae-315">8</span></span>|  
  
### <a name="ftp-task"></a><span data-ttu-id="bc0ae-316">FTP タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-316">FTP Task</span></span>  
 <span data-ttu-id="bc0ae-317">`Operation`列挙体の値を使用してプロパティを設定し `DTSFTPOp` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-317">`Operation` property-Set by using values from the `DTSFTPOp` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-318">DTSFTPOp の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-318">Friendly name in DTSFTPOp</span></span>|<span data-ttu-id="bc0ae-319">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-319">Numeric value</span></span>|  
|-------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-320">Send</span><span class="sxs-lookup"><span data-stu-id="bc0ae-320">Send</span></span>|<span data-ttu-id="bc0ae-321">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-321">0</span></span>|  
|<span data-ttu-id="bc0ae-322">受信</span><span class="sxs-lookup"><span data-stu-id="bc0ae-322">Receive</span></span>|<span data-ttu-id="bc0ae-323">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-323">1</span></span>|  
|<span data-ttu-id="bc0ae-324">DeleteLocal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-324">DeleteLocal</span></span>|<span data-ttu-id="bc0ae-325">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-325">2</span></span>|  
|<span data-ttu-id="bc0ae-326">DeleteRemote</span><span class="sxs-lookup"><span data-stu-id="bc0ae-326">DeleteRemote</span></span>|<span data-ttu-id="bc0ae-327">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-327">3</span></span>|  
|<span data-ttu-id="bc0ae-328">MakeDirLocal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-328">MakeDirLocal</span></span>|<span data-ttu-id="bc0ae-329">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-329">4</span></span>|  
|<span data-ttu-id="bc0ae-330">MakeDirRemote</span><span class="sxs-lookup"><span data-stu-id="bc0ae-330">MakeDirRemote</span></span>|<span data-ttu-id="bc0ae-331">5</span><span class="sxs-lookup"><span data-stu-id="bc0ae-331">5</span></span>|  
|<span data-ttu-id="bc0ae-332">RemoveDirLocal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-332">RemoveDirLocal</span></span>|<span data-ttu-id="bc0ae-333">6</span><span class="sxs-lookup"><span data-stu-id="bc0ae-333">6</span></span>|  
|<span data-ttu-id="bc0ae-334">RemoveDirRemote</span><span class="sxs-lookup"><span data-stu-id="bc0ae-334">RemoveDirRemote</span></span>|<span data-ttu-id="bc0ae-335">7</span><span class="sxs-lookup"><span data-stu-id="bc0ae-335">7</span></span>|  
  
### <a name="message-queue-task"></a><span data-ttu-id="bc0ae-336">Message Queue Task</span><span class="sxs-lookup"><span data-stu-id="bc0ae-336">Message Queue Task</span></span>  
 <span data-ttu-id="bc0ae-337">`MessageType`列挙体の値を使用してプロパティを設定し `MQMessageType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-337">`MessageType` property-Set by using values from the `MQMessageType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-338">MQMessageType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-338">Friendly name in MQMessageType</span></span>|<span data-ttu-id="bc0ae-339">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-339">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-340">DTSMQMessageType_String</span><span class="sxs-lookup"><span data-stu-id="bc0ae-340">DTSMQMessageType_String</span></span>|<span data-ttu-id="bc0ae-341">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-341">0</span></span>|  
|<span data-ttu-id="bc0ae-342">DTSMQMessageType_DataFile</span><span class="sxs-lookup"><span data-stu-id="bc0ae-342">DTSMQMessageType_DataFile</span></span>|<span data-ttu-id="bc0ae-343">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-343">1</span></span>|  
|<span data-ttu-id="bc0ae-344">DTSMQMessageType_Variables</span><span class="sxs-lookup"><span data-stu-id="bc0ae-344">DTSMQMessageType_Variables</span></span>|<span data-ttu-id="bc0ae-345">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-345">2</span></span>|  
|<span data-ttu-id="bc0ae-346">DTSMQMessagType_StringMessageToVariable</span><span class="sxs-lookup"><span data-stu-id="bc0ae-346">DTSMQMessagType_StringMessageToVariable</span></span>|<span data-ttu-id="bc0ae-347">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-347">3</span></span>|  
  
 <span data-ttu-id="bc0ae-348">`StringCompareType`列挙体の値を使用してプロパティを設定し `MQStringMessageCompare` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-348">`StringCompareType` property-Set by using values from the `MQStringMessageCompare` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-349">MQStringMessageCompare の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-349">Friendly name in MQStringMessageCompare</span></span>|<span data-ttu-id="bc0ae-350">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-350">Numeric value</span></span>|  
|---------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-351">DTSMQStringMessageCompare_None</span><span class="sxs-lookup"><span data-stu-id="bc0ae-351">DTSMQStringMessageCompare_None</span></span>|<span data-ttu-id="bc0ae-352">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-352">0</span></span>|  
|<span data-ttu-id="bc0ae-353">DTSMQStringMessageCompare_Exact</span><span class="sxs-lookup"><span data-stu-id="bc0ae-353">DTSMQStringMessageCompare_Exact</span></span>|<span data-ttu-id="bc0ae-354">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-354">1</span></span>|  
|<span data-ttu-id="bc0ae-355">DTSMQStringMessageCompare_IgnoreCase</span><span class="sxs-lookup"><span data-stu-id="bc0ae-355">DTSMQStringMessageCompare_IgnoreCase</span></span>|<span data-ttu-id="bc0ae-356">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-356">2</span></span>|  
|<span data-ttu-id="bc0ae-357">DTSMQStringMessageCompare_Contains</span><span class="sxs-lookup"><span data-stu-id="bc0ae-357">DTSMQStringMessageCompare_Contains</span></span>|<span data-ttu-id="bc0ae-358">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-358">3</span></span>|  
  
 <span data-ttu-id="bc0ae-359">`TaskType`列挙体の値を使用してプロパティを設定し `MQType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-359">`TaskType` property-Set by using values from the `MQType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-360">MQType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-360">Friendly name in MQType</span></span>|<span data-ttu-id="bc0ae-361">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-361">Numeric value</span></span>|  
|-----------------------------|-------------------|  
|<span data-ttu-id="bc0ae-362">DTSMQType_Sender</span><span class="sxs-lookup"><span data-stu-id="bc0ae-362">DTSMQType_Sender</span></span>|<span data-ttu-id="bc0ae-363">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-363">0</span></span>|  
|<span data-ttu-id="bc0ae-364">DTSMQType_Receiver</span><span class="sxs-lookup"><span data-stu-id="bc0ae-364">DTSMQType_Receiver</span></span>|<span data-ttu-id="bc0ae-365">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-365">1</span></span>|  
  
### <a name="send-mail-task"></a><span data-ttu-id="bc0ae-366">メール送信タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-366">Send Mail Task</span></span>  
 <span data-ttu-id="bc0ae-367">`MessageSourceType`列挙体の値を使用してプロパティを設定し `SendMailMessageSourceType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-367">`MessageSourceType` property-Set by using values from the `SendMailMessageSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-368">SendMailMessageSourceType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-368">Friendly Name in SendMailMessageSourceType</span></span>|<span data-ttu-id="bc0ae-369">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-369">Numeric Value</span></span>|  
|------------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-370">DirectInput</span><span class="sxs-lookup"><span data-stu-id="bc0ae-370">DirectInput</span></span>|<span data-ttu-id="bc0ae-371">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-371">0</span></span>|  
|<span data-ttu-id="bc0ae-372">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-372">FileConnection</span></span>|<span data-ttu-id="bc0ae-373">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-373">1</span></span>|  
|<span data-ttu-id="bc0ae-374">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-374">Variable</span></span>|<span data-ttu-id="bc0ae-375">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-375">2</span></span>|  
  
 <span data-ttu-id="bc0ae-376">`Priority`列挙体の値を使用してプロパティを設定し `MailPriority` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-376">`Priority` property-Set by using values from the `MailPriority` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-377">MailPriority の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-377">Friendly Name in MailPriority</span></span>|<span data-ttu-id="bc0ae-378">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-378">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-379">高</span><span class="sxs-lookup"><span data-stu-id="bc0ae-379">High</span></span>|<span data-ttu-id="bc0ae-380">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-380">1</span></span>|  
|<span data-ttu-id="bc0ae-381">Normal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-381">Normal</span></span>|<span data-ttu-id="bc0ae-382">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-382">3</span></span>|  
|<span data-ttu-id="bc0ae-383">低</span><span class="sxs-lookup"><span data-stu-id="bc0ae-383">Low</span></span>|<span data-ttu-id="bc0ae-384">5</span><span class="sxs-lookup"><span data-stu-id="bc0ae-384">5</span></span>|  
  
### <a name="transfer-database-task"></a><span data-ttu-id="bc0ae-385">データベース転送タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-385">Transfer Database Task</span></span>  
 <span data-ttu-id="bc0ae-386">`Action`列挙体の値を使用してプロパティを設定し `TransferAction` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-386">`Action` property-Set by using values from the `TransferAction` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-387">TransferAction の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-387">Friendly name in TransferAction</span></span>|<span data-ttu-id="bc0ae-388">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-388">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-389">コピー</span><span class="sxs-lookup"><span data-stu-id="bc0ae-389">Copy</span></span>|<span data-ttu-id="bc0ae-390">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-390">0</span></span>|  
|<span data-ttu-id="bc0ae-391">[詳細ビュー]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-391">Move</span></span>|<span data-ttu-id="bc0ae-392">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-392">1</span></span>|  
  
 <span data-ttu-id="bc0ae-393">`Method`列挙体の値を使用してプロパティを設定し `TransferMethod` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-393">`Method` property-Set by using values from the `TransferMethod` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-394">TransferMethod の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-394">Friendly name in TransferMethod</span></span>|<span data-ttu-id="bc0ae-395">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-395">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-396">DatabaseOffline</span><span class="sxs-lookup"><span data-stu-id="bc0ae-396">DatabaseOffline</span></span>|<span data-ttu-id="bc0ae-397">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-397">0</span></span>|  
|<span data-ttu-id="bc0ae-398">DatabaseOnline</span><span class="sxs-lookup"><span data-stu-id="bc0ae-398">DatabaseOnline</span></span>|<span data-ttu-id="bc0ae-399">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-399">1</span></span>|  
  
### <a name="transfer-error-messages-task"></a><span data-ttu-id="bc0ae-400">エラー メッセージ転送タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-400">Transfer Error Messages Task</span></span>  
 <span data-ttu-id="bc0ae-401">`IfObjectExists`列挙体の値を使用してプロパティを設定し `IfObjectExists` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-401">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-402">IfObjectExists の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-402">Friendly Name in IfObjectExists</span></span>|<span data-ttu-id="bc0ae-403">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-403">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-404">[FailTask]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-404">FailTask</span></span>|<span data-ttu-id="bc0ae-405">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-405">0</span></span>|  
|<span data-ttu-id="bc0ae-406">Overwrite</span><span class="sxs-lookup"><span data-stu-id="bc0ae-406">Overwrite</span></span>|<span data-ttu-id="bc0ae-407">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-407">1</span></span>|  
|<span data-ttu-id="bc0ae-408">Skip</span><span class="sxs-lookup"><span data-stu-id="bc0ae-408">Skip</span></span>|<span data-ttu-id="bc0ae-409">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-409">2</span></span>|  
  
### <a name="transfer-jobs-task"></a><span data-ttu-id="bc0ae-410">ジョブ転送タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-410">Transfer Jobs Task</span></span>  
 <span data-ttu-id="bc0ae-411">`IfObjectExists`列挙体の値を使用してプロパティを設定し `IfObjectExists` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-411">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-412">IfObjectExists の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-412">Friendly Name in IfObjectExists</span></span>|<span data-ttu-id="bc0ae-413">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-413">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-414">[FailTask]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-414">FailTask</span></span>|<span data-ttu-id="bc0ae-415">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-415">0</span></span>|  
|<span data-ttu-id="bc0ae-416">Overwrite</span><span class="sxs-lookup"><span data-stu-id="bc0ae-416">Overwrite</span></span>|<span data-ttu-id="bc0ae-417">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-417">1</span></span>|  
|<span data-ttu-id="bc0ae-418">Skip</span><span class="sxs-lookup"><span data-stu-id="bc0ae-418">Skip</span></span>|<span data-ttu-id="bc0ae-419">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-419">2</span></span>|  
  
### <a name="transfer-logins-task"></a><span data-ttu-id="bc0ae-420">ログイン転送タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-420">Transfer Logins Task</span></span>  
 <span data-ttu-id="bc0ae-421">`IfObjectExists`列挙体の値を使用してプロパティを設定し `IfObjectExists` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-421">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-422">IfObjectExists の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-422">Friendly name in IfObjectExists</span></span>|<span data-ttu-id="bc0ae-423">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-423">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-424">[FailTask]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-424">FailTask</span></span>|<span data-ttu-id="bc0ae-425">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-425">0</span></span>|  
|<span data-ttu-id="bc0ae-426">Overwrite</span><span class="sxs-lookup"><span data-stu-id="bc0ae-426">Overwrite</span></span>|<span data-ttu-id="bc0ae-427">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-427">1</span></span>|  
|<span data-ttu-id="bc0ae-428">Skip</span><span class="sxs-lookup"><span data-stu-id="bc0ae-428">Skip</span></span>|<span data-ttu-id="bc0ae-429">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-429">2</span></span>|  
  
 <span data-ttu-id="bc0ae-430">`LoginsToTransfer`列挙体の値を使用してプロパティを設定し `LoginsToTransfer` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-430">`LoginsToTransfer` property-Set by using values from the `LoginsToTransfer` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-431">LoginsToTransfer の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-431">Friendly name in LoginsToTransfer</span></span>|<span data-ttu-id="bc0ae-432">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-432">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-433">[AllLogins]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-433">AllLogins</span></span>|<span data-ttu-id="bc0ae-434">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-434">0</span></span>|  
|<span data-ttu-id="bc0ae-435">[SelectedLogins]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-435">SelectedLogins</span></span>|<span data-ttu-id="bc0ae-436">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-436">1</span></span>|  
|<span data-ttu-id="bc0ae-437">[AllLoginsFromSelectedDatabases]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-437">AllLoginsFromSelectedDatabases</span></span>|<span data-ttu-id="bc0ae-438">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-438">2</span></span>|  
  
### <a name="transfer-master-stored-procedures-task"></a><span data-ttu-id="bc0ae-439">Master ストアド プロシージャ転送タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-439">Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="bc0ae-440">`IfObjectExists`列挙体の値を使用してプロパティを設定し `IfObjectExists` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-440">`IfObjectExists` property-Set by using values from the `IfObjectExists` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-441">IfObjectExists の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-441">Friendly name in IfObjectExists</span></span>|<span data-ttu-id="bc0ae-442">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-442">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-443">[FailTask]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-443">FailTask</span></span>|<span data-ttu-id="bc0ae-444">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-444">0</span></span>|  
|<span data-ttu-id="bc0ae-445">Overwrite</span><span class="sxs-lookup"><span data-stu-id="bc0ae-445">Overwrite</span></span>|<span data-ttu-id="bc0ae-446">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-446">1</span></span>|  
|<span data-ttu-id="bc0ae-447">Skip</span><span class="sxs-lookup"><span data-stu-id="bc0ae-447">Skip</span></span>|<span data-ttu-id="bc0ae-448">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-448">2</span></span>|  
  
### <a name="transfer-sql-server-objects-task"></a><span data-ttu-id="bc0ae-449">SQL Server オブジェクトの転送タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-449">Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="bc0ae-450">`ExistingData`列挙体の値を使用してプロパティを設定し `ExistingData` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-450">`ExistingData` property-Set by using values from the `ExistingData` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-451">ExistingData の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-451">Friendly name in ExistingData</span></span>|<span data-ttu-id="bc0ae-452">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-452">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-453">Replace</span><span class="sxs-lookup"><span data-stu-id="bc0ae-453">Replace</span></span>|<span data-ttu-id="bc0ae-454">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-454">0</span></span>|  
|<span data-ttu-id="bc0ae-455">Append</span><span class="sxs-lookup"><span data-stu-id="bc0ae-455">Append</span></span>|<span data-ttu-id="bc0ae-456">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-456">1</span></span>|  
  
### <a name="web-service-task"></a><span data-ttu-id="bc0ae-457">Web サービス タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-457">Web Service Task</span></span>  
 <span data-ttu-id="bc0ae-458">`OutputType`列挙体の値を使用してプロパティを設定し `DTSOutputType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-458">`OutputType` property-Set by using values from the `DTSOutputType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-459">DTSOutputType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-459">Friendly name in DTSOutputType</span></span>|<span data-ttu-id="bc0ae-460">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-460">Numeric value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-461">ファイル</span><span class="sxs-lookup"><span data-stu-id="bc0ae-461">File</span></span>|<span data-ttu-id="bc0ae-462">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-462">0</span></span>|  
|<span data-ttu-id="bc0ae-463">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-463">Variable</span></span>|<span data-ttu-id="bc0ae-464">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-464">1</span></span>|  
  
### <a name="wmi-data-reader-task"></a><span data-ttu-id="bc0ae-465">WMI データ リーダー タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-465">WMI Data Reader Task</span></span>  
 <span data-ttu-id="bc0ae-466">`OverwriteDestination`列挙体の値を使用してプロパティを設定し `OverwriteDestination` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-466">`OverwriteDestination` property-Set by using values from the `OverwriteDestination` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-467">OverwriteDestination の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-467">Friendly name in OverwriteDestination</span></span>|<span data-ttu-id="bc0ae-468">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-468">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-469">OverwriteDestination</span><span class="sxs-lookup"><span data-stu-id="bc0ae-469">OverwriteDestination</span></span>|<span data-ttu-id="bc0ae-470">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-470">0</span></span>|  
|<span data-ttu-id="bc0ae-471">AppendToDestination</span><span class="sxs-lookup"><span data-stu-id="bc0ae-471">AppendToDestination</span></span>|<span data-ttu-id="bc0ae-472">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-472">1</span></span>|  
|<span data-ttu-id="bc0ae-473">KeepOriginal</span><span class="sxs-lookup"><span data-stu-id="bc0ae-473">KeepOriginal</span></span>|<span data-ttu-id="bc0ae-474">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-474">2</span></span>|  
  
 <span data-ttu-id="bc0ae-475">`OutputType`列挙体の値を使用してプロパティを設定し `OutputType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-475">`OutputType` property-Set by using values from the `OutputType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-476">OutputType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-476">Friendly name in OutputType</span></span>|<span data-ttu-id="bc0ae-477">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-477">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-478">DataTable</span><span class="sxs-lookup"><span data-stu-id="bc0ae-478">DataTable</span></span>|<span data-ttu-id="bc0ae-479">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-479">0</span></span>|  
|<span data-ttu-id="bc0ae-480">PropertyValue</span><span class="sxs-lookup"><span data-stu-id="bc0ae-480">PropertyValue</span></span>|<span data-ttu-id="bc0ae-481">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-481">1</span></span>|  
|<span data-ttu-id="bc0ae-482">PropertyNameAndValue</span><span class="sxs-lookup"><span data-stu-id="bc0ae-482">PropertyNameAndValue</span></span>|<span data-ttu-id="bc0ae-483">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-483">2</span></span>|  
  
 <span data-ttu-id="bc0ae-484">`DestinationType`列挙体の値を使用してプロパティを設定し `DestinationType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-484">`DestinationType` property-Set by using values from the `DestinationType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-485">DestinationType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-485">Friendly name in DestinationType</span></span>|<span data-ttu-id="bc0ae-486">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-486">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-487">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-487">FileConnection</span></span>|<span data-ttu-id="bc0ae-488">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-488">0</span></span>|  
|<span data-ttu-id="bc0ae-489">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-489">Variable</span></span>|<span data-ttu-id="bc0ae-490">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-490">1</span></span>|  
  
 <span data-ttu-id="bc0ae-491">`WqlQuerySourceType`列挙体の値を使用してプロパティを設定し `QuerySourceType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-491">`WqlQuerySourceType` property-Set by using values from the `QuerySourceType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-492">QuerySourceType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-492">Friendly Name in QuerySourceType</span></span>|<span data-ttu-id="bc0ae-493">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-493">Numeric Value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-494">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-494">FileConnection</span></span>|<span data-ttu-id="bc0ae-495">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-495">0</span></span>|  
|<span data-ttu-id="bc0ae-496">DirectInput</span><span class="sxs-lookup"><span data-stu-id="bc0ae-496">DirectInput</span></span>|<span data-ttu-id="bc0ae-497">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-497">1</span></span>|  
|<span data-ttu-id="bc0ae-498">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-498">Variable</span></span>|<span data-ttu-id="bc0ae-499">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-499">2</span></span>|  
  
 <span data-ttu-id="bc0ae-500">WMI イベント監視の `ActionAtEvent` プロパティ-列挙の値を使用して設定さ `ActionAtEvent` れます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-500">WMI Event Watcher `ActionAtEvent` property-Set by using values from the `ActionAtEvent` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-501">ActionAtEvent の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-501">Friendly Name in ActionAtEvent</span></span>|<span data-ttu-id="bc0ae-502">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-502">Numeric Value</span></span>|  
|------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-503">LogTheEventAndFireDTSEvent</span><span class="sxs-lookup"><span data-stu-id="bc0ae-503">LogTheEventAndFireDTSEvent</span></span>|<span data-ttu-id="bc0ae-504">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-504">0</span></span>|  
|<span data-ttu-id="bc0ae-505">LogTheEvent</span><span class="sxs-lookup"><span data-stu-id="bc0ae-505">LogTheEvent</span></span>|<span data-ttu-id="bc0ae-506">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-506">1</span></span>|  
  
 <span data-ttu-id="bc0ae-507">`ActionAtTimeout`列挙体の値を使用してプロパティを設定し `ActionAtTimeout` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-507">`ActionAtTimeout` property-Set by using values from the `ActionAtTimeout` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-508">ActionAtTimeout の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-508">Friendly name in ActionAtTimeout</span></span>|<span data-ttu-id="bc0ae-509">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-509">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-510">LogTimeoutAndFireDTSEvent</span><span class="sxs-lookup"><span data-stu-id="bc0ae-510">LogTimeoutAndFireDTSEvent</span></span>|<span data-ttu-id="bc0ae-511">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-511">0</span></span>|  
|<span data-ttu-id="bc0ae-512">LogTimeout</span><span class="sxs-lookup"><span data-stu-id="bc0ae-512">LogTimeout</span></span>|<span data-ttu-id="bc0ae-513">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-513">1</span></span>|  
  
 <span data-ttu-id="bc0ae-514">`AfterEvent`列挙体の値を使用してプロパティを設定し `AfterEvent` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-514">`AfterEvent` property-Set by using values from the `AfterEvent` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-515">AfterEvent の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-515">Friendly name in AfterEvent</span></span>|<span data-ttu-id="bc0ae-516">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-516">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-517">ReturnWithSuccess</span><span class="sxs-lookup"><span data-stu-id="bc0ae-517">ReturnWithSuccess</span></span>|<span data-ttu-id="bc0ae-518">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-518">0</span></span>|  
|<span data-ttu-id="bc0ae-519">ReturnWithFailure</span><span class="sxs-lookup"><span data-stu-id="bc0ae-519">ReturnWithFailure</span></span>|<span data-ttu-id="bc0ae-520">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-520">1</span></span>|  
|<span data-ttu-id="bc0ae-521">WatchfortheEventAgain</span><span class="sxs-lookup"><span data-stu-id="bc0ae-521">WatchfortheEventAgain</span></span>|<span data-ttu-id="bc0ae-522">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-522">2</span></span>|  
  
 <span data-ttu-id="bc0ae-523">`AfterTimeout`列挙体の値を使用してプロパティを設定し `AfterTimeout` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-523">`AfterTimeout` property-Set by using values from the `AfterTimeout` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-524">AfterTimeout の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-524">Friendly name in AfterTimeout</span></span>|<span data-ttu-id="bc0ae-525">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-525">Numeric value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-526">ReturnWithSuccess</span><span class="sxs-lookup"><span data-stu-id="bc0ae-526">ReturnWithSuccess</span></span>|<span data-ttu-id="bc0ae-527">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-527">0</span></span>|  
|<span data-ttu-id="bc0ae-528">ReturnWithFailure</span><span class="sxs-lookup"><span data-stu-id="bc0ae-528">ReturnWithFailure</span></span>|<span data-ttu-id="bc0ae-529">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-529">1</span></span>|  
|<span data-ttu-id="bc0ae-530">WatchfortheEventAgain</span><span class="sxs-lookup"><span data-stu-id="bc0ae-530">WatchfortheEventAgain</span></span>|<span data-ttu-id="bc0ae-531">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-531">2</span></span>|  
  
 <span data-ttu-id="bc0ae-532">`WqlQuerySourceType`列挙体の値を使用してプロパティを設定し `QuerySourceType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-532">`WqlQuerySourceType` property-Set by using values from the `QuerySourceType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-533">QuerySourceType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-533">Friendly name in QuerySourceType</span></span>|<span data-ttu-id="bc0ae-534">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-534">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-535">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-535">FileConnection</span></span>|<span data-ttu-id="bc0ae-536">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-536">0</span></span>|  
|<span data-ttu-id="bc0ae-537">DirectInput</span><span class="sxs-lookup"><span data-stu-id="bc0ae-537">DirectInput</span></span>|<span data-ttu-id="bc0ae-538">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-538">1</span></span>|  
|<span data-ttu-id="bc0ae-539">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-539">Variable</span></span>|<span data-ttu-id="bc0ae-540">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-540">2</span></span>|  
  
### <a name="xml-task"></a><span data-ttu-id="bc0ae-541">XML タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-541">XML Task</span></span>  
 <span data-ttu-id="bc0ae-542">`OperationType`列挙体の値を使用してプロパティを設定し `DTSXMLOperation` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-542">`OperationType` property-Set by using values from the `DTSXMLOperation` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-543">DTSXMLOperation の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-543">Friendly name in DTSXMLOperation</span></span>|<span data-ttu-id="bc0ae-544">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-544">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-545">検証</span><span class="sxs-lookup"><span data-stu-id="bc0ae-545">Validate</span></span>|<span data-ttu-id="bc0ae-546">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-546">0</span></span>|  
|<span data-ttu-id="bc0ae-547">XSLT (XSLT)</span><span class="sxs-lookup"><span data-stu-id="bc0ae-547">XSLT</span></span>|<span data-ttu-id="bc0ae-548">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-548">1</span></span>|  
|<span data-ttu-id="bc0ae-549">[XPath]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-549">XPATH</span></span>|<span data-ttu-id="bc0ae-550">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-550">2</span></span>|  
|<span data-ttu-id="bc0ae-551">Merge</span><span class="sxs-lookup"><span data-stu-id="bc0ae-551">Merge</span></span>|<span data-ttu-id="bc0ae-552">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-552">3</span></span>|  
|<span data-ttu-id="bc0ae-553">[Diff]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-553">Diff</span></span>|<span data-ttu-id="bc0ae-554">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-554">4</span></span>|  
|<span data-ttu-id="bc0ae-555">修正プログラム</span><span class="sxs-lookup"><span data-stu-id="bc0ae-555">Patch</span></span>|<span data-ttu-id="bc0ae-556">5</span><span class="sxs-lookup"><span data-stu-id="bc0ae-556">5</span></span>|  
  
 <span data-ttu-id="bc0ae-557">`SourceType`、 `SecondOperandType` 、およびの各 `XPathSourceType` プロパティ-列挙の値を使用して設定さ `DTSXMLSourceType` れます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-557">`SourceType`, `SecondOperandType`, and `XPathSourceType` properties-Set by using values from the `DTSXMLSourceType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-558">DTSXMLSourceType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-558">Friendly name in DTSXMLSourceType</span></span>|<span data-ttu-id="bc0ae-559">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-559">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-560">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-560">FileConnection</span></span>|<span data-ttu-id="bc0ae-561">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-561">0</span></span>|  
|<span data-ttu-id="bc0ae-562">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-562">Variable</span></span>|<span data-ttu-id="bc0ae-563">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-563">1</span></span>|  
|<span data-ttu-id="bc0ae-564">DirectInput</span><span class="sxs-lookup"><span data-stu-id="bc0ae-564">DirectInput</span></span>|<span data-ttu-id="bc0ae-565">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-565">2</span></span>|  
  
 <span data-ttu-id="bc0ae-566">`DestinationType`および**DiffGramDestinationType**プロパティ-列挙の値を使用して設定し `DTSXMLSaveResultTo` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-566">`DestinationType` and **DiffGramDestinationType** properties-Set by using values from the `DTSXMLSaveResultTo` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-567">DTSXMLSaveResultTo の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-567">Friendly name in DTSXMLSaveResultTo</span></span>|<span data-ttu-id="bc0ae-568">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-568">Numeric value</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-569">[FileConnection]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-569">FileConnection</span></span>|<span data-ttu-id="bc0ae-570">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-570">0</span></span>|  
|<span data-ttu-id="bc0ae-571">変数</span><span class="sxs-lookup"><span data-stu-id="bc0ae-571">Variable</span></span>|<span data-ttu-id="bc0ae-572">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-572">1</span></span>|  
  
 <span data-ttu-id="bc0ae-573">`ValidationType`列挙体の値を使用してプロパティを設定し `DTSXMLValidationType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-573">`ValidationType` property-Set by using values from the `DTSXMLValidationType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-574">DTSXMLValidationType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-574">Friendly name in DTSXMLValidationType</span></span>|<span data-ttu-id="bc0ae-575">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-575">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-576">[DTD]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-576">DTD</span></span>|<span data-ttu-id="bc0ae-577">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-577">0</span></span>|  
|<span data-ttu-id="bc0ae-578">[XSD]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-578">XSD</span></span>|<span data-ttu-id="bc0ae-579">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-579">1</span></span>|  
  
 <span data-ttu-id="bc0ae-580">`XPathOperation`列挙体の値を使用してプロパティを設定し `DTSXMLXPathOperation` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-580">`XPathOperation` property-Set by using values from the `DTSXMLXPathOperation` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-581">DTSXMLXPathOperation の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-581">Friendly name in DTSXMLXPathOperation</span></span>|<span data-ttu-id="bc0ae-582">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-582">Numeric Value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-583">評価</span><span class="sxs-lookup"><span data-stu-id="bc0ae-583">Evaluation</span></span>|<span data-ttu-id="bc0ae-584">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-584">0</span></span>|  
|<span data-ttu-id="bc0ae-585">値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-585">Values</span></span>|<span data-ttu-id="bc0ae-586">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-586">1</span></span>|  
|<span data-ttu-id="bc0ae-587">NodeList</span><span class="sxs-lookup"><span data-stu-id="bc0ae-587">NodeList</span></span>|<span data-ttu-id="bc0ae-588">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-588">2</span></span>|  
  
 <span data-ttu-id="bc0ae-589">`DiffOptions`列挙体の値を使用してプロパティを設定し `DTSXMLDiffOptions` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-589">`DiffOptions` property-Set by using values from the `DTSXMLDiffOptions` enumeration.</span></span> <span data-ttu-id="bc0ae-590">この列挙子の各オプションは相互排他的ではなく、複数を同時に指定することができます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-590">The options in this enumerator are not mutually exclusive.</span></span> <span data-ttu-id="bc0ae-591">複数のオプションを使用するには、適用するオプションをコンマ区切りのリストで指定します。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-591">To use multiple options, provide a comma-separated list of the options to apply.</span></span>  
  
|<span data-ttu-id="bc0ae-592">DTSXMLDiffOptions の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-592">Friendly name in DTSXMLDiffOptions</span></span>|<span data-ttu-id="bc0ae-593">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-593">Numeric Value</span></span>|  
|----------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-594">なし</span><span class="sxs-lookup"><span data-stu-id="bc0ae-594">None</span></span>|<span data-ttu-id="bc0ae-595">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-595">0</span></span>|  
|<span data-ttu-id="bc0ae-596">IgnoreChildOrder</span><span class="sxs-lookup"><span data-stu-id="bc0ae-596">IgnoreChildOrder</span></span>|<span data-ttu-id="bc0ae-597">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-597">1</span></span>|  
|<span data-ttu-id="bc0ae-598">[IgnoreComments]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-598">IgnoreComments</span></span>|<span data-ttu-id="bc0ae-599">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-599">2</span></span>|  
|<span data-ttu-id="bc0ae-600">IgnorePI</span><span class="sxs-lookup"><span data-stu-id="bc0ae-600">IgnorePI</span></span>|<span data-ttu-id="bc0ae-601">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-601">4</span></span>|  
|<span data-ttu-id="bc0ae-602">IgnoreWhitespace</span><span class="sxs-lookup"><span data-stu-id="bc0ae-602">IgnoreWhitespace</span></span>|<span data-ttu-id="bc0ae-603">8</span><span class="sxs-lookup"><span data-stu-id="bc0ae-603">8</span></span>|  
|<span data-ttu-id="bc0ae-604">[IgnoreNamespaces]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-604">IgnoreNamespaces</span></span>|<span data-ttu-id="bc0ae-605">16</span><span class="sxs-lookup"><span data-stu-id="bc0ae-605">16</span></span>|  
|<span data-ttu-id="bc0ae-606">[IgnorePrefixes]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-606">IgnorePrefixes</span></span>|<span data-ttu-id="bc0ae-607">32</span><span class="sxs-lookup"><span data-stu-id="bc0ae-607">32</span></span>|  
|<span data-ttu-id="bc0ae-608">IgnoreXmlDecl</span><span class="sxs-lookup"><span data-stu-id="bc0ae-608">IgnoreXmlDecl</span></span>|<span data-ttu-id="bc0ae-609">64</span><span class="sxs-lookup"><span data-stu-id="bc0ae-609">64</span></span>|  
|<span data-ttu-id="bc0ae-610">IgnoreDtd</span><span class="sxs-lookup"><span data-stu-id="bc0ae-610">IgnoreDtd</span></span>|<span data-ttu-id="bc0ae-611">128</span><span class="sxs-lookup"><span data-stu-id="bc0ae-611">128</span></span>|  
  
 <span data-ttu-id="bc0ae-612">`DiffAlgorithm`列挙体の値を使用してプロパティを設定し `DTSXMLDiffAlgorithm` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-612">`DiffAlgorithm` property-Set by using values from the `DTSXMLDiffAlgorithm` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-613">DTSXMLDiffAlgorithm の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-613">Friendly name in DTSXMLDiffAlgorithm</span></span>|<span data-ttu-id="bc0ae-614">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-614">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-615">Auto</span><span class="sxs-lookup"><span data-stu-id="bc0ae-615">Auto</span></span>|<span data-ttu-id="bc0ae-616">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-616">0</span></span>|  
|<span data-ttu-id="bc0ae-617">速い</span><span class="sxs-lookup"><span data-stu-id="bc0ae-617">Fast</span></span>|<span data-ttu-id="bc0ae-618">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-618">1</span></span>|  
|<span data-ttu-id="bc0ae-619">[詳細]</span><span class="sxs-lookup"><span data-stu-id="bc0ae-619">Precise</span></span>|<span data-ttu-id="bc0ae-620">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-620">2</span></span>|  
  
##  <a name="maintenance-plan-tasks"></a><a name="MaintenancePlanTasks"></a> <span data-ttu-id="bc0ae-621">メンテナンス プランのタスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-621">Maintenance Plan Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="bc0ae-622">には、メンテナンス プランおよび [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ用の SQL Server タスクを実行する一連のタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-622">includes a set of tasks that perform SQL Server tasks for use in maintenance plans and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bc0ae-623">では、プログラムによるこれらのタスクの操作がサポートされていません。また、プログラミング リファレンス ドキュメントには、これらのタスクとその列挙子に関する API ドキュメントが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-623">does not support working with these tasks programmatically and programming reference documentation does not include API documentation of these tasks and their enumerators.</span></span>  
  
### <a name="all-maintenance-tasks"></a><span data-ttu-id="bc0ae-624">すべてのメンテナンス タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-624">All Maintenance Tasks</span></span>  
 <span data-ttu-id="bc0ae-625">すべてのメンテナンス タスクでは、次の列挙子を使用して、指定したプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-625">All maintenance tasks use the following enumerations to set the specified properties.</span></span>  
  
 <span data-ttu-id="bc0ae-626">`DatabaseSelectionType`列挙体の値を使用してプロパティを設定し `DatabaseSelection` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-626">`DatabaseSelectionType` property-Set by using values from the `DatabaseSelection` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-627">DatabaseSelection の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-627">Friendly name in DatabaseSelection</span></span>|<span data-ttu-id="bc0ae-628">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-628">Numeric value</span></span>|  
|----------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-629">なし</span><span class="sxs-lookup"><span data-stu-id="bc0ae-629">None</span></span>|<span data-ttu-id="bc0ae-630">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-630">0</span></span>|  
|<span data-ttu-id="bc0ae-631">All</span><span class="sxs-lookup"><span data-stu-id="bc0ae-631">All</span></span>|<span data-ttu-id="bc0ae-632">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-632">1</span></span>|  
|<span data-ttu-id="bc0ae-633">システム</span><span class="sxs-lookup"><span data-stu-id="bc0ae-633">System</span></span>|<span data-ttu-id="bc0ae-634">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-634">2</span></span>|  
|<span data-ttu-id="bc0ae-635">User</span><span class="sxs-lookup"><span data-stu-id="bc0ae-635">User</span></span>|<span data-ttu-id="bc0ae-636">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-636">3</span></span>|  
|<span data-ttu-id="bc0ae-637">固有</span><span class="sxs-lookup"><span data-stu-id="bc0ae-637">Specific</span></span>|<span data-ttu-id="bc0ae-638">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-638">4</span></span>|  
  
 <span data-ttu-id="bc0ae-639">`TableSelectionType`列挙体の値を使用してプロパティを設定し `TableSelection` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-639">`TableSelectionType` property-Set by using values from the `TableSelection` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-640">TableSelection の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-640">Friendly name in TableSelection</span></span>|<span data-ttu-id="bc0ae-641">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-641">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-642">なし</span><span class="sxs-lookup"><span data-stu-id="bc0ae-642">None</span></span>|<span data-ttu-id="bc0ae-643">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-643">0</span></span>|  
|<span data-ttu-id="bc0ae-644">All</span><span class="sxs-lookup"><span data-stu-id="bc0ae-644">All</span></span>|<span data-ttu-id="bc0ae-645">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-645">1</span></span>|  
|<span data-ttu-id="bc0ae-646">固有</span><span class="sxs-lookup"><span data-stu-id="bc0ae-646">Specific</span></span>|<span data-ttu-id="bc0ae-647">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-647">2</span></span>|  
  
 <span data-ttu-id="bc0ae-648">`ObjectTypeSelection`列挙体の値を使用してプロパティを設定し `ObjectType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-648">`ObjectTypeSelection` property-Set by using values from the `ObjectType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-649">ObjectType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-649">Friendly name in ObjectType</span></span>|<span data-ttu-id="bc0ae-650">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-650">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-651">テーブル</span><span class="sxs-lookup"><span data-stu-id="bc0ae-651">Table</span></span>|<span data-ttu-id="bc0ae-652">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-652">0</span></span>|  
|<span data-ttu-id="bc0ae-653">表示</span><span class="sxs-lookup"><span data-stu-id="bc0ae-653">View</span></span>|<span data-ttu-id="bc0ae-654">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-654">1</span></span>|  
|<span data-ttu-id="bc0ae-655">TableView</span><span class="sxs-lookup"><span data-stu-id="bc0ae-655">TableView</span></span>|<span data-ttu-id="bc0ae-656">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-656">2</span></span>|  
  
### <a name="back-up-database-task"></a><span data-ttu-id="bc0ae-657">データベースのバックアップ タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-657">Back Up Database Task</span></span>  
 <span data-ttu-id="bc0ae-658">`DestinationCreationType`列挙体の値を使用してプロパティを設定し `DestinationType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-658">`DestinationCreationType` property-Set by using values from the `DestinationType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-659">DestinationType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-659">Friendly name in DestinationType</span></span>|<span data-ttu-id="bc0ae-660">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-660">Numeric value</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-661">Auto</span><span class="sxs-lookup"><span data-stu-id="bc0ae-661">Auto</span></span>|<span data-ttu-id="bc0ae-662">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-662">0</span></span>|  
|<span data-ttu-id="bc0ae-663">マニュアル</span><span class="sxs-lookup"><span data-stu-id="bc0ae-663">Manual</span></span>|<span data-ttu-id="bc0ae-664">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-664">1</span></span>|  
  
 <span data-ttu-id="bc0ae-665">`ExistingBackupsAction`列挙体の値を使用してプロパティを設定し `ActionForExistingBackups` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-665">`ExistingBackupsAction` property-Set by using values from the `ActionForExistingBackups` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-666">ActionForExistingBackups の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-666">Friendly name in ActionForExistingBackups</span></span>|<span data-ttu-id="bc0ae-667">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-667">Numeric value</span></span>|  
|-----------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-668">Append</span><span class="sxs-lookup"><span data-stu-id="bc0ae-668">Append</span></span>|<span data-ttu-id="bc0ae-669">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-669">0</span></span>|  
|<span data-ttu-id="bc0ae-670">Overwrite</span><span class="sxs-lookup"><span data-stu-id="bc0ae-670">Overwrite</span></span>|<span data-ttu-id="bc0ae-671">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-671">1</span></span>|  
  
 <span data-ttu-id="bc0ae-672">`BackupAction`列挙体の値を使用してプロパティを設定し `BackupTaskType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-672">`BackupAction` property-Set by using values from the `BackupTaskType` enumeration.</span></span> <span data-ttu-id="bc0ae-673">このプロパティは、タスクで実行されるバックアップの種類を定義する際に、`BackupIsIncremental` プロパティと合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-673">This property works with the `BackupIsIncremental` property to define the type of backup that the task performs.</span></span>  
  
|<span data-ttu-id="bc0ae-674">BackupTaskType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-674">Friendly name in BackupTaskType</span></span>|<span data-ttu-id="bc0ae-675">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-675">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-676">データベース</span><span class="sxs-lookup"><span data-stu-id="bc0ae-676">Database</span></span>|<span data-ttu-id="bc0ae-677">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-677">0</span></span>|  
|<span data-ttu-id="bc0ae-678">ファイル</span><span class="sxs-lookup"><span data-stu-id="bc0ae-678">Files</span></span>|<span data-ttu-id="bc0ae-679">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-679">1</span></span>|  
|<span data-ttu-id="bc0ae-680">ログ</span><span class="sxs-lookup"><span data-stu-id="bc0ae-680">Log</span></span>|<span data-ttu-id="bc0ae-681">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-681">2</span></span>|  
  
 <span data-ttu-id="bc0ae-682">`BackupDevice`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) 列挙の値を使用してプロパティを設定し `DeviceType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-682">`BackupDevice` property-Set by using values from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `DeviceType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-683">DeviceType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-683">Friendly name in DeviceType</span></span>|<span data-ttu-id="bc0ae-684">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-684">Numeric value</span></span>|  
|---------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-685">LogicalDevice</span><span class="sxs-lookup"><span data-stu-id="bc0ae-685">LogicalDevice</span></span>|<span data-ttu-id="bc0ae-686">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-686">0</span></span>|  
|<span data-ttu-id="bc0ae-687">Tape</span><span class="sxs-lookup"><span data-stu-id="bc0ae-687">Tape</span></span>|<span data-ttu-id="bc0ae-688">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-688">1</span></span>|  
|<span data-ttu-id="bc0ae-689">ファイル</span><span class="sxs-lookup"><span data-stu-id="bc0ae-689">File</span></span>|<span data-ttu-id="bc0ae-690">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-690">2</span></span>|  
|<span data-ttu-id="bc0ae-691">Pipe</span><span class="sxs-lookup"><span data-stu-id="bc0ae-691">Pipe</span></span>|<span data-ttu-id="bc0ae-692">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-692">3</span></span>|  
|<span data-ttu-id="bc0ae-693">VirtualDevice</span><span class="sxs-lookup"><span data-stu-id="bc0ae-693">VirtualDevice</span></span>|<span data-ttu-id="bc0ae-694">4</span><span class="sxs-lookup"><span data-stu-id="bc0ae-694">4</span></span>|  
  
### <a name="maintenance-cleanup-task"></a><span data-ttu-id="bc0ae-695">メンテナンス クリーンアップ タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-695">Maintenance Cleanup Task</span></span>  
 <span data-ttu-id="bc0ae-696">`FileTypeSelected`列挙体の値を使用してプロパティを設定し `FileType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-696">`FileTypeSelected` property-Set by using values from the `FileType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-697">FileType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-697">Friendly name in FileType</span></span>|<span data-ttu-id="bc0ae-698">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-698">Numeric value</span></span>|  
|-------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-699">FileBackup</span><span class="sxs-lookup"><span data-stu-id="bc0ae-699">FileBackup</span></span>|<span data-ttu-id="bc0ae-700">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-700">0</span></span>|  
|<span data-ttu-id="bc0ae-701">FileReport</span><span class="sxs-lookup"><span data-stu-id="bc0ae-701">FileReport</span></span>|<span data-ttu-id="bc0ae-702">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-702">1</span></span>|  
  
 <span data-ttu-id="bc0ae-703">`OlderThanTimeUnitType`列挙体の値を使用してプロパティを設定し `TimeUnitType` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-703">`OlderThanTimeUnitType` property-Set by using values from the `TimeUnitType` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-704">TimeUnitType の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-704">Friendly Name in TimeUnitType</span></span>|<span data-ttu-id="bc0ae-705">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-705">Numeric Value</span></span>|  
|-----------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-706">日</span><span class="sxs-lookup"><span data-stu-id="bc0ae-706">Day</span></span>|<span data-ttu-id="bc0ae-707">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-707">0</span></span>|  
|<span data-ttu-id="bc0ae-708">Week</span><span class="sxs-lookup"><span data-stu-id="bc0ae-708">Week</span></span>|<span data-ttu-id="bc0ae-709">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-709">1</span></span>|  
|<span data-ttu-id="bc0ae-710">Month</span><span class="sxs-lookup"><span data-stu-id="bc0ae-710">Month</span></span>|<span data-ttu-id="bc0ae-711">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-711">2</span></span>|  
|<span data-ttu-id="bc0ae-712">年</span><span class="sxs-lookup"><span data-stu-id="bc0ae-712">Year</span></span>|<span data-ttu-id="bc0ae-713">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-713">3</span></span>|  
  
### <a name="update-statistics-task"></a><span data-ttu-id="bc0ae-714">統計の更新タスク</span><span class="sxs-lookup"><span data-stu-id="bc0ae-714">Update Statistics Task</span></span>  
 <span data-ttu-id="bc0ae-715">`UpdateType`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) 列挙の値を使用してプロパティを設定し `StatisticsTarget` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-715">`UpdateType` property-Set by using values from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `StatisticsTarget` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-716">StatisticsTarget の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-716">Friendly name in StatisticsTarget</span></span>|<span data-ttu-id="bc0ae-717">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-717">Numeric value</span></span>|  
|---------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-718">列</span><span class="sxs-lookup"><span data-stu-id="bc0ae-718">Column</span></span>|<span data-ttu-id="bc0ae-719">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-719">1</span></span>|  
|<span data-ttu-id="bc0ae-720">インデックス</span><span class="sxs-lookup"><span data-stu-id="bc0ae-720">Index</span></span>|<span data-ttu-id="bc0ae-721">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-721">2</span></span>|  
|<span data-ttu-id="bc0ae-722">All</span><span class="sxs-lookup"><span data-stu-id="bc0ae-722">All</span></span>|<span data-ttu-id="bc0ae-723">3</span><span class="sxs-lookup"><span data-stu-id="bc0ae-723">3</span></span>|  
  
##  <a name="common-properties"></a><a name="CommonProperties"></a> <span data-ttu-id="bc0ae-724">共通プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc0ae-724">Common Properties</span></span>  
 <span data-ttu-id="bc0ae-725">パッケージ、タスク、Foreach ループ コンテナー、For ループ コンテナー、およびシーケンス コンテナーでは、次の列挙子を使用して、指定されたプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-725">Packages, tasks, and the Foreach Loop, For Loop, and Sequence containers can use the following enumerations to set the specified properties.</span></span>  
  
 <span data-ttu-id="bc0ae-726">`ForceExecutionResult`列挙体の値を使用してプロパティを設定し `DTSForcedExecResult` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-726">`ForceExecutionResult` property-Set by using values from the `DTSForcedExecResult` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-727">DTSForcedExecResult の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-727">Friendly name in DTSForcedExecResult</span></span>|<span data-ttu-id="bc0ae-728">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-728">Numeric value</span></span>|  
|------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-729">なし</span><span class="sxs-lookup"><span data-stu-id="bc0ae-729">None</span></span>|<span data-ttu-id="bc0ae-730">-1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-730">-1</span></span>|  
|<span data-ttu-id="bc0ae-731">Success</span><span class="sxs-lookup"><span data-stu-id="bc0ae-731">Success</span></span>|<span data-ttu-id="bc0ae-732">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-732">0</span></span>|  
|<span data-ttu-id="bc0ae-733">障害</span><span class="sxs-lookup"><span data-stu-id="bc0ae-733">Failure</span></span>|<span data-ttu-id="bc0ae-734">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-734">1</span></span>|  
|<span data-ttu-id="bc0ae-735">Completion</span><span class="sxs-lookup"><span data-stu-id="bc0ae-735">Completion</span></span>|<span data-ttu-id="bc0ae-736">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-736">2</span></span>|  
  
 <span data-ttu-id="bc0ae-737">`IsolationLevel`プロパティ-.NET Framework 列挙体によって設定さ `IsolationLevel` れます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-737">`IsolationLevel` property-Set by the .NET Framework `IsolationLevel` enumeration.</span></span> <span data-ttu-id="bc0ae-738">詳細については、 [MSDN ライブラリ](https://go.microsoft.com/fwlink?LinkId=17313)の .NET Framework クラス ライブラリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-738">For more information, see the .NET Framework Class Library in the [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313).</span></span>  
  
 <span data-ttu-id="bc0ae-739">`LoggingMode`列挙体の値を使用してプロパティを設定し `DTSLoggingMode` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-739">`LoggingMode` property-Set by using values from the `DTSLoggingMode` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-740">DTSLoggingMode の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-740">Friendly name in DTSLoggingMode</span></span>|<span data-ttu-id="bc0ae-741">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-741">Numeric value</span></span>|  
|-------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-742">UseParentSetting</span><span class="sxs-lookup"><span data-stu-id="bc0ae-742">UseParentSetting</span></span>|<span data-ttu-id="bc0ae-743">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-743">0</span></span>|  
|<span data-ttu-id="bc0ae-744">有効</span><span class="sxs-lookup"><span data-stu-id="bc0ae-744">Enabled</span></span>|<span data-ttu-id="bc0ae-745">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-745">1</span></span>|  
|<span data-ttu-id="bc0ae-746">無効</span><span class="sxs-lookup"><span data-stu-id="bc0ae-746">Disabled</span></span>|<span data-ttu-id="bc0ae-747">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-747">2</span></span>|  
  
 <span data-ttu-id="bc0ae-748">`TransactionOption`列挙体の値を使用してプロパティを設定し `DTSTransactionOption` ます。</span><span class="sxs-lookup"><span data-stu-id="bc0ae-748">`TransactionOption` property-Set by using values from the `DTSTransactionOption` enumeration.</span></span>  
  
|<span data-ttu-id="bc0ae-749">DTSTransactionOption の表示名</span><span class="sxs-lookup"><span data-stu-id="bc0ae-749">Friendly name in DTSTransactionOption</span></span>|<span data-ttu-id="bc0ae-750">数値</span><span class="sxs-lookup"><span data-stu-id="bc0ae-750">Numeric value</span></span>|  
|-------------------------------------------|-------------------|  
|<span data-ttu-id="bc0ae-751">NotSupported</span><span class="sxs-lookup"><span data-stu-id="bc0ae-751">NotSupported</span></span>|<span data-ttu-id="bc0ae-752">0</span><span class="sxs-lookup"><span data-stu-id="bc0ae-752">0</span></span>|  
|<span data-ttu-id="bc0ae-753">サポートされています</span><span class="sxs-lookup"><span data-stu-id="bc0ae-753">Supported</span></span>|<span data-ttu-id="bc0ae-754">1</span><span class="sxs-lookup"><span data-stu-id="bc0ae-754">1</span></span>|  
|<span data-ttu-id="bc0ae-755">必須</span><span class="sxs-lookup"><span data-stu-id="bc0ae-755">Required</span></span>|<span data-ttu-id="bc0ae-756">2</span><span class="sxs-lookup"><span data-stu-id="bc0ae-756">2</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="bc0ae-757">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bc0ae-757">Related Tasks</span></span>  
 [<span data-ttu-id="bc0ae-758">プロパティ式を追加または変更する</span><span class="sxs-lookup"><span data-stu-id="bc0ae-758">Add or Change a Property Expression</span></span>](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc0ae-759">参照</span><span class="sxs-lookup"><span data-stu-id="bc0ae-759">See Also</span></span>  
 <span data-ttu-id="bc0ae-760">[パッケージでプロパティ式を使用する](use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="bc0ae-760">[Use Property Expressions in Packages](use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="bc0ae-761">[Integration Services &#40;SSIS&#41; パッケージ](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="bc0ae-761">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 <span data-ttu-id="bc0ae-762">[Integration Services コンテナー](../control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="bc0ae-762">[Integration Services Containers](../control-flow/integration-services-containers.md) </span></span>  
 <span data-ttu-id="bc0ae-763">[Integration Services タスク](../control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bc0ae-763">[Integration Services Tasks](../control-flow/integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="bc0ae-764">優先順位制約</span><span class="sxs-lookup"><span data-stu-id="bc0ae-764">Precedence Constraints</span></span>](../control-flow/precedence-constraints.md)  
  
  
