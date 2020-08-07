---
title: RDL サンドボックスを有効または無効にする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d5619e9f-ec5b-4376-9b34-1f74de6fade7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7af1477751093862c99d00978278315e600511e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719617"
---
# <a name="enable-and-disable-rdl-sandboxing"></a><span data-ttu-id="a7091-102">RDL サンドボックスの有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="a7091-102">Enable and Disable RDL Sandboxing</span></span>
  <span data-ttu-id="a7091-103">RDL (レポート定義言語) サンドボックス機能を使用すると、複数のテナントが 1 つのレポート サーバー Web ファームを使用している環境で、個々のテナントによる特定の種類のリソースの使用を検出および制限できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a7091-103">The RDL (Report Definition Language) Sandboxing feature lets you detect and restrict the usage of specific types of resources, by individual tenants, in an environment of multiple tenants that use a single web farm of report servers.</span></span> <span data-ttu-id="a7091-104">このような例として、複数のテナントまたは複数の企業によって使用される単一のレポート サーバー Web ファームを管理するホスティング サービスのシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="a7091-104">An example of this is a hosting services scenario where you might maintain a single web farm of report servers that are used by multiple tenants, and perhaps different companies.</span></span> <span data-ttu-id="a7091-105">レポート サーバー管理者は、次の目的を達成するためにこの機能を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="a7091-105">As a report server administrator, you can enable this feature to help achieve the following objectives:</span></span>  
  
-   <span data-ttu-id="a7091-106">外部リソースのサイズを制限する。</span><span class="sxs-lookup"><span data-stu-id="a7091-106">Restrict external resource sizes.</span></span> <span data-ttu-id="a7091-107">外部リソースには、画像、.xslt ファイル、およびマップ データが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a7091-107">External resources include images, .xslt files, and map data.</span></span>  
  
-   <span data-ttu-id="a7091-108">レポートのパブリッシュ時に、式のテキストで使用される型およびメンバーを制限する。</span><span class="sxs-lookup"><span data-stu-id="a7091-108">At report publish time, limit types and members that are used in expression text.</span></span>  
  
-   <span data-ttu-id="a7091-109">レポートの処理時に、テキストの長さおよび式の戻り値のサイズを制限する。</span><span class="sxs-lookup"><span data-stu-id="a7091-109">At report processing time, limit the length of the text and the size of the return value for expressions.</span></span>  
  
 <span data-ttu-id="a7091-110">RDL サンドボックスが有効になると、次の機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="a7091-110">When RDL Sandboxing is enabled, the following features are disabled:</span></span>  
  
-   <span data-ttu-id="a7091-111">**\<Code>** レポート定義の要素内のカスタムコード。</span><span class="sxs-lookup"><span data-stu-id="a7091-111">Custom code in the **\<Code>** element of a report definition.</span></span>  
  
-   <span data-ttu-id="a7091-112">[!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] カスタム レポート アイテムに対する RDL の下位互換性モード。</span><span class="sxs-lookup"><span data-stu-id="a7091-112">RDL backward compatibility mode for [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] custom report items.</span></span>  
  
-   <span data-ttu-id="a7091-113">式での名前付きパラメーター。</span><span class="sxs-lookup"><span data-stu-id="a7091-113">Named parameters in expressions.</span></span>  
  
 <span data-ttu-id="a7091-114">このトピックでは、RSReportServer.Config ファイルの <> 要素内の各要素について説明し `RDLSandboxing` ます。</span><span class="sxs-lookup"><span data-stu-id="a7091-114">This topic describes each element in the <`RDLSandboxing`> element in the RSReportServer.Config file.</span></span> <span data-ttu-id="a7091-115">このファイルの編集の詳細については、「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7091-115">For more information about how to modify this file, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span> <span data-ttu-id="a7091-116">RDL サンドボックス機能に関連した操作は、サーバー トレース ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="a7091-116">A server trace log records activity related to the RDL Sandboxing feature.</span></span> <span data-ttu-id="a7091-117">トレース ログの詳細については、「 [レポート サーバー サービスのトレース ログ](report-server/report-server-service-trace-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7091-117">For more information about trace logs, see [Report Server Service Trace Log](report-server/report-server-service-trace-log.md).</span></span>  
  
## <a name="example-configuration"></a><span data-ttu-id="a7091-118">構成の例</span><span class="sxs-lookup"><span data-stu-id="a7091-118">Example Configuration</span></span>  
 <span data-ttu-id="a7091-119">次の例は、RSReportServer.Config ファイルの <> 要素の設定と例の値を示して `RDLSandboxing` います。</span><span class="sxs-lookup"><span data-stu-id="a7091-119">The following example shows the settings and example values for the <`RDLSandboxing`> element in the RSReportServer.Config file.</span></span>  
  
```  
<RDLSandboxing>  
   <MaxExpressionLength>5000</MaxExpressionLength>  
   <MaxResourceSize>5000</MaxResourceSize>  
   <MaxStringResultLength>3000</MaxStringResultLength>  
   <MaxArrayResultLength>250</MaxArrayResultLength>  
   <Types>  
      <Allow Namespace="System.Drawing" AllowNew="True">Bitmap</Allow>  
      <Allow Namespace="TypeConverters.Custom" AllowNew="True">*</Allow>  
   </Types>  
   <Members>  
      <Deny>Format</Deny>  
      <Deny>StrDup</Deny>  
   </Members>  
</RDLSandboxing>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="a7091-120">構成設定</span><span class="sxs-lookup"><span data-stu-id="a7091-120">Configuration Settings</span></span>  
 <span data-ttu-id="a7091-121">次の表では、構成設定に関する情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a7091-121">The following table provides information about configuration settings.</span></span> <span data-ttu-id="a7091-122">構成ファイルに出現する順に、設定を示します。</span><span class="sxs-lookup"><span data-stu-id="a7091-122">Settings are presented in the order in which they appear in the configuration file.</span></span>  
  
|<span data-ttu-id="a7091-123">設定</span><span class="sxs-lookup"><span data-stu-id="a7091-123">Setting</span></span>|<span data-ttu-id="a7091-124">Description</span><span class="sxs-lookup"><span data-stu-id="a7091-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7091-125">**MaxExpressionLength**</span><span class="sxs-lookup"><span data-stu-id="a7091-125">**MaxExpressionLength**</span></span>|<span data-ttu-id="a7091-126">RDL 式で許可される文字数の最大値です。</span><span class="sxs-lookup"><span data-stu-id="a7091-126">Maximum number of characters allowed in RDL expressions.</span></span><br /><br /> <span data-ttu-id="a7091-127">既定: 1000</span><span class="sxs-lookup"><span data-stu-id="a7091-127">Default: 1000</span></span>|  
|<span data-ttu-id="a7091-128">**MaxResourceSize**</span><span class="sxs-lookup"><span data-stu-id="a7091-128">**MaxResourceSize**</span></span>|<span data-ttu-id="a7091-129">外部リソースに許可されるサイズの最大値 (単位: KB) です。</span><span class="sxs-lookup"><span data-stu-id="a7091-129">Maximum number of KB allowed for an external resource.</span></span><br /><br /> <span data-ttu-id="a7091-130">既定値: 100</span><span class="sxs-lookup"><span data-stu-id="a7091-130">Default: 100</span></span>|  
|<span data-ttu-id="a7091-131">**MaxStringResultLength**</span><span class="sxs-lookup"><span data-stu-id="a7091-131">**MaxStringResultLength**</span></span>|<span data-ttu-id="a7091-132">RDL 式の戻り値で許可される文字数の最大値です。</span><span class="sxs-lookup"><span data-stu-id="a7091-132">Maximum number of characters allowed in a return value for an RDL expression.</span></span><br /><br /> <span data-ttu-id="a7091-133">既定: 1000</span><span class="sxs-lookup"><span data-stu-id="a7091-133">Default: 1000</span></span>|  
|<span data-ttu-id="a7091-134">**MaxArrayResultLength**</span><span class="sxs-lookup"><span data-stu-id="a7091-134">**MaxArrayResultLength**</span></span>|<span data-ttu-id="a7091-135">RDL 式の配列戻り値で許可されるアイテム数の最大値です。</span><span class="sxs-lookup"><span data-stu-id="a7091-135">Maximum number of items allowed in an array return value for an RDL expression.</span></span><br /><br /> <span data-ttu-id="a7091-136">既定値: 100</span><span class="sxs-lookup"><span data-stu-id="a7091-136">Default: 100</span></span>|  
|<span data-ttu-id="a7091-137">**型**</span><span class="sxs-lookup"><span data-stu-id="a7091-137">**Types**</span></span>|<span data-ttu-id="a7091-138">RDL 式内で許可されるメンバーの一覧です。</span><span class="sxs-lookup"><span data-stu-id="a7091-138">The list of members to allow within RDL expressions.</span></span>|  
|<span data-ttu-id="a7091-139">**許可**</span><span class="sxs-lookup"><span data-stu-id="a7091-139">**Allow**</span></span>|<span data-ttu-id="a7091-140">RDL 式で許可される型または型のセットです。</span><span class="sxs-lookup"><span data-stu-id="a7091-140">A type or set of types to allow in RDL expressions.</span></span>|  
|<span data-ttu-id="a7091-141">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="a7091-141">**Namespace**</span></span>|<span data-ttu-id="a7091-142">**Allow** の属性の 1 つであり、Value に適用される 1 つ以上の型を含む名前空間です。</span><span class="sxs-lookup"><span data-stu-id="a7091-142">Attribute for **Allow** that is the namespace that contains one or more types that apply to Value.</span></span> <span data-ttu-id="a7091-143">このプロパティでは、大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="a7091-143">This property is case-insensitive.</span></span>|  
|`AllowNew`|<span data-ttu-id="a7091-144">**Allow**のブール属性で、型の新しいインスタンスを rdl 式と rdl 要素のどちらで作成できるかを制御し **\<Class>** ます。</span><span class="sxs-lookup"><span data-stu-id="a7091-144">Boolean attribute for **Allow** that controls whether new instances of the type are allowed to be created in RDL expressions or in an RDL **\<Class>** element.</span></span><br /><br /> <span data-ttu-id="a7091-145">注: `RDLSandboxing` が有効になっている場合、の設定に関係なく、RDL 式に新しい配列を作成することはできません `AllowNew` 。</span><span class="sxs-lookup"><span data-stu-id="a7091-145">Note: When `RDLSandboxing` is enabled, new arrays cannot be created in RDL expressions, regardless of the setting of `AllowNew`.</span></span>|  
|<span data-ttu-id="a7091-146">**Value**</span><span class="sxs-lookup"><span data-stu-id="a7091-146">**Value**</span></span>|<span data-ttu-id="a7091-147">**Allow** に対する値であり、RDL 式で許可される型の名前を示します。</span><span class="sxs-lookup"><span data-stu-id="a7091-147">Value for **Allow** that is the name of the type to allow in RDL expressions.</span></span> <span data-ttu-id="a7091-148">値は、 **\*** 名前空間のすべての型が許可されることを示します。</span><span class="sxs-lookup"><span data-stu-id="a7091-148">The value **\*** indicates that all types in the namespace are allowed.</span></span> <span data-ttu-id="a7091-149">このプロパティでは、大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="a7091-149">This property is case-insensitive.</span></span>|  
|<span data-ttu-id="a7091-150">**メンバー**</span><span class="sxs-lookup"><span data-stu-id="a7091-150">**Members**</span></span>|<span data-ttu-id="a7091-151">要素に含まれる型の一覧については、 **\<Types>** RDL 式で許可されないメンバー名の一覧があります。</span><span class="sxs-lookup"><span data-stu-id="a7091-151">For the list of types that are include in the **\<Types>** element, the list of member names that are not allowed in RDL expressions.</span></span>|  
|<span data-ttu-id="a7091-152">**Deny**</span><span class="sxs-lookup"><span data-stu-id="a7091-152">**Deny**</span></span>|<span data-ttu-id="a7091-153">RDL 式で許可されないメンバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="a7091-153">The name of a member that is not allowed in RDL expressions.</span></span> <span data-ttu-id="a7091-154">このプロパティでは、大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="a7091-154">This property is case-insensitive.</span></span><br /><br /> <span data-ttu-id="a7091-155">注: メンバーに対して **Deny** が指定されている場合、この名前を持つすべての型のメンバーがすべて許可されません。</span><span class="sxs-lookup"><span data-stu-id="a7091-155">Note: When **Deny** is specified for a member, all members with this name for all types are not allowed.</span></span>|  
  
## <a name="working-with-expressions-when-rdl-sandboxing-is-enabled"></a><span data-ttu-id="a7091-156">RDL サンドボックスが有効なときの式の操作</span><span class="sxs-lookup"><span data-stu-id="a7091-156">Working with Expressions when RDL Sandboxing is Enabled</span></span>  
 <span data-ttu-id="a7091-157">式で使用されるリソースの管理を容易にするために、RDL サンドボックス機能を次のような方法で変更できます。</span><span class="sxs-lookup"><span data-stu-id="a7091-157">You can modify the RDL Sandboxing feature to help manage the resources that are used by an expression in the following ways:</span></span>  
  
-   <span data-ttu-id="a7091-158">式に使用する文字数を制限する。</span><span class="sxs-lookup"><span data-stu-id="a7091-158">Restrict the number of characters that are used for an expression.</span></span>  
  
-   <span data-ttu-id="a7091-159">式から返される結果のサイズを制限する。</span><span class="sxs-lookup"><span data-stu-id="a7091-159">Restrict the size of the result returned by an expression.</span></span>  
  
-   <span data-ttu-id="a7091-160">式での使用を許可する特定の型の一覧を指定する。</span><span class="sxs-lookup"><span data-stu-id="a7091-160">Allow a specific list of types that can be used in an expression.</span></span>  
  
-   <span data-ttu-id="a7091-161">式での使用を許可された型の一覧に対して、制限するメンバーの一覧を名前で指定する。</span><span class="sxs-lookup"><span data-stu-id="a7091-161">Restrict the list of members by name for the list of allowed types that can be used in an expression.</span></span>  
  
-   <span data-ttu-id="a7091-162">RDL サンドボックス機能では、承認する型の一覧と拒否するメンバーの一覧を作成できます。</span><span class="sxs-lookup"><span data-stu-id="a7091-162">The RDL Sandboxing feature enables you to create a list of approved types and a list of denied members.</span></span> <span data-ttu-id="a7091-163">承認する型の一覧を許可一覧と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a7091-163">The list of approved types is called an allow list.</span></span> <span data-ttu-id="a7091-164">拒否するメンバーの一覧をブロック一覧と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a7091-164">The list of denied members is called a block list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7091-165">レポート定義では、式のリファレンスの各インスタンスの型をコンピューターが知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="a7091-165">In the report definition, a computer cannot know the type of each instances of an expression reference.</span></span> <span data-ttu-id="a7091-166">ブロック一覧にメンバーを追加すると、許可一覧に含まれるすべての型について、その名前を持つすべてのメンバーが拒否されます。</span><span class="sxs-lookup"><span data-stu-id="a7091-166">When you add a member to the block list, you are denying all members of that name across all types in the allow list.</span></span>  
  
 <span data-ttu-id="a7091-167">RDL 式の結果は、実行時に検証されます。</span><span class="sxs-lookup"><span data-stu-id="a7091-167">RDL expression results are verified at run time.</span></span> <span data-ttu-id="a7091-168">RDL 式は、レポートのパブリッシュ時にレポート定義で検証されます。</span><span class="sxs-lookup"><span data-stu-id="a7091-168">RDL expressions are verified in the report definition when the report is published.</span></span> <span data-ttu-id="a7091-169">レポート サーバーのトレース ログで、違反がないかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a7091-169">Monitor the report server trace log for violations.</span></span> <span data-ttu-id="a7091-170">詳細については、「 [Report Server Service Trace Log](report-server/report-server-service-trace-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7091-170">For more information, see [Report Server Service Trace Log](report-server/report-server-service-trace-log.md).</span></span>  
  
### <a name="working-with-types"></a><span data-ttu-id="a7091-171">型の操作</span><span class="sxs-lookup"><span data-stu-id="a7091-171">Working with Types</span></span>  
 <span data-ttu-id="a7091-172">許可一覧に型を追加することで、RDL 式にアクセスする次のエントリ ポイントを制御できます。</span><span class="sxs-lookup"><span data-stu-id="a7091-172">When you add a type to the allow list, you are controlling the following entry points to access RDL expressions:</span></span>  
  
-   <span data-ttu-id="a7091-173">型の静的メンバー</span><span class="sxs-lookup"><span data-stu-id="a7091-173">Static members of a type.</span></span>  
  
-   <span data-ttu-id="a7091-174">[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` メソッド。</span><span class="sxs-lookup"><span data-stu-id="a7091-174">The [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` method.</span></span>  
  
-   <span data-ttu-id="a7091-175">**\<Classes>** レポート定義内の要素。</span><span class="sxs-lookup"><span data-stu-id="a7091-175">The **\<Classes>** element in the report definition.</span></span>  
  
-   <span data-ttu-id="a7091-176">許可一覧に含まれる型に対してブロック一覧に追加したメンバー</span><span class="sxs-lookup"><span data-stu-id="a7091-176">Members that you have added to the block list for a type in the allow list.</span></span>  
  
 <span data-ttu-id="a7091-177">許可一覧では、次のエントリ ポイントは制御されません。</span><span class="sxs-lookup"><span data-stu-id="a7091-177">The allow list does not control the following entry points:</span></span>  
  
-   <span data-ttu-id="a7091-178">レポート データセット。</span><span class="sxs-lookup"><span data-stu-id="a7091-178">Report datasets.</span></span> <span data-ttu-id="a7091-179">クエリから返されるレポート データセット内のフィールドは、任意の有効な RDL 型を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="a7091-179">Fields in report datasets that are returned from queries might contain any valid RDL type.</span></span>  
  
-   <span data-ttu-id="a7091-180">レポート パラメーター。</span><span class="sxs-lookup"><span data-stu-id="a7091-180">Report parameters.</span></span> <span data-ttu-id="a7091-181">ユーザーから提供されるパラメーターの値は、任意の有効な RDL 型を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="a7091-181">User-supplied parameter values might contain any valid RDL type.</span></span>  
  
-   <span data-ttu-id="a7091-182">ブロック一覧に含まれていない、有効な型のメンバー。</span><span class="sxs-lookup"><span data-stu-id="a7091-182">Members of an enabled type that are not in the block list.</span></span> <span data-ttu-id="a7091-183">既定では、許可一覧に含まれるすべての型のすべてのメンバーが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="a7091-183">By default, all members of all types in the allow list are enabled.</span></span> <span data-ttu-id="a7091-184">ブロック一覧にメンバー名を追加すると、許可一覧に含まれるすべての型について、その名前を持つすべてのメンバーが拒否されます。</span><span class="sxs-lookup"><span data-stu-id="a7091-184">When you add a member name to the block list, you are denying all members with that name across all types that are in the allow list.</span></span>  
  
 <span data-ttu-id="a7091-185">1 つの型のメンバーを有効にして、別の型では同じ名前のメンバーを拒否するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7091-185">To enable a member of one type but deny a member with the same name for a different type, you must do the following:</span></span>  
  
-   <span data-ttu-id="a7091-186">**\<Deny>** メンバー名の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="a7091-186">Add a **\<Deny>** element for the member name.</span></span>  
  
-   <span data-ttu-id="a7091-187">有効にするメンバーに対して、カスタム アセンブリのクラスに異なる名前のプロキシ メンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7091-187">Create a proxy member with a different name on a class in a custom assembly for the member that you want to enable.</span></span>  
  
-   <span data-ttu-id="a7091-188">その新しいクラスを許可一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="a7091-188">Add that new class to the allow list.</span></span>  
  
 <span data-ttu-id="a7091-189">許可一覧に [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の関数を追加するには、Microsoft.VisualBasic 名前空間の対応する型を許可一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="a7091-189">To add [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework functions to the allow list, add the corresponding types from the Microsoft.VisualBasic namespace to the allow list.</span></span>  
  
 <span data-ttu-id="a7091-190">許可一覧に [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の型キーワードを追加するには、対応する CLR 型を許可一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="a7091-190">To add [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework type keywords to the allow list, add the corresponding CLR type to the allow list.</span></span> <span data-ttu-id="a7091-191">たとえば、.NET Framework キーワードを使用するには、 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Integer` 要素に次の XML フラグメントを追加し **\<RDLSandboxing>** ます。</span><span class="sxs-lookup"><span data-stu-id="a7091-191">For example, to use the [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework keyword `Integer`, add the following XML fragment to the **\<RDLSandboxing>** element:</span></span>  
  
```  
<Allow Namespace="System">Int32</Allow>  
```  
  
 <span data-ttu-id="a7091-192">許可一覧にジェネリック型または [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の NULL 値を許容する型を追加するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a7091-192">To add a generic or a [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework nullable type to the allow list, you must do the following:</span></span>  
  
-   <span data-ttu-id="a7091-193">ジェネリック型または [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の NULL 値を許容する型に対してプロキシ型を作成します。</span><span class="sxs-lookup"><span data-stu-id="a7091-193">Create a proxy type for the generic or [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework nullable type.</span></span>  
  
-   <span data-ttu-id="a7091-194">そのプロキシ型を許可一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="a7091-194">Add the proxy type to the allow list.</span></span>  
  
 <span data-ttu-id="a7091-195">カスタム アセンブリから許可一覧に型を追加しても、アセンブリに対して暗黙に実行権限が付与されることはありません。</span><span class="sxs-lookup"><span data-stu-id="a7091-195">Adding a type from a custom assembly to the allow list does not implicitly grant execute permission on the assembly.</span></span> <span data-ttu-id="a7091-196">コード アクセス セキュリティ ファイルを具体的に変更して、アセンブリに実行権限を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7091-196">You must specifically modify the code access security file and provide execute permission to your assembly.</span></span> <span data-ttu-id="a7091-197">詳細については、「 [Reporting Services のコード アクセス セキュリティ](extensions/secure-development/code-access-security-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7091-197">For more information, see [Code Access Security in Reporting Services](extensions/secure-development/code-access-security-in-reporting-services.md).</span></span>  
  
#### <a name="maintaining-the-deny-list-of-members"></a><span data-ttu-id="a7091-198">\<Deny>メンバーの一覧の管理</span><span class="sxs-lookup"><span data-stu-id="a7091-198">Maintaining the \<Deny> List of Members</span></span>  
 <span data-ttu-id="a7091-199">許可一覧に新しい型を追加するときには、次に示す場合に、メンバーのブロック一覧の更新が必要となります。</span><span class="sxs-lookup"><span data-stu-id="a7091-199">When you add a new type to the allow list, use the following list to determine when you might have to update the block list of members:</span></span>  
  
-   <span data-ttu-id="a7091-200">新しい型を導入するバージョンでカスタム アセンブリを更新する場合。</span><span class="sxs-lookup"><span data-stu-id="a7091-200">When you update a custom assembly with a version that introduces new types.</span></span>  
  
-   <span data-ttu-id="a7091-201">許可一覧に含まれる型にメンバーを追加する場合。</span><span class="sxs-lookup"><span data-stu-id="a7091-201">When you add members to the types in the allow list.</span></span>  
  
-   <span data-ttu-id="a7091-202">レポート サーバー上で [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] を更新する場合。</span><span class="sxs-lookup"><span data-stu-id="a7091-202">When you update the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] on the report server.</span></span>  
  
-   <span data-ttu-id="a7091-203">レポート サーバーを [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]の新しいバージョンにアップグレードする場合。</span><span class="sxs-lookup"><span data-stu-id="a7091-203">When you upgrade the report server to a later version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a7091-204">RDL 型に新しいメンバーが追加された可能性があるため、新しい RDL スキーマを処理できるようにレポート サーバーを更新する場合</span><span class="sxs-lookup"><span data-stu-id="a7091-204">When you update a report server to handle a later RDL schema, because new members might have been added to RDL types.</span></span>  
  
### <a name="working-with-operators-and-new"></a><span data-ttu-id="a7091-205">演算子と New の操作</span><span class="sxs-lookup"><span data-stu-id="a7091-205">Working with Operators and New</span></span>  
 <span data-ttu-id="a7091-206">既定では、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の言語演算子は、`New` を除いて常に許可されます。</span><span class="sxs-lookup"><span data-stu-id="a7091-206">By default, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework language operators, except for `New`, are always allowed.</span></span> <span data-ttu-id="a7091-207">`New`演算子は、要素の属性によって制御され `AllowNew` **\<Allow>** ます。</span><span class="sxs-lookup"><span data-stu-id="a7091-207">The `New` operator is controlled by the `AllowNew` attribute on the **\<Allow>** element.</span></span> <span data-ttu-id="a7091-208">既定のコレクションアクセサー演算子やなどの .NET Framework キャストマクロなど、その他の言語演算子 `!` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `CInt` は常に許可されます。</span><span class="sxs-lookup"><span data-stu-id="a7091-208">Other language operators, such as the default collection accessor operator `!` and [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework cast macros such as `CInt`, are always allowed.</span></span>  
  
 <span data-ttu-id="a7091-209">カスタム演算子を含め、ブロック一覧への演算子の追加はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a7091-209">Adding operators to a block list, including custom operators, is not supported.</span></span> <span data-ttu-id="a7091-210">特定の型に対して演算子を除外するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7091-210">To exclude operators for a type, you must do the following:</span></span>  
  
-   <span data-ttu-id="a7091-211">除外する演算子を実装しないプロキシ型を作成します。</span><span class="sxs-lookup"><span data-stu-id="a7091-211">Create a proxy type that does not implement the operators that you want to exclude.</span></span>  
  
-   <span data-ttu-id="a7091-212">そのプロキシ型を許可一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="a7091-212">Add the proxy type to the allow list.</span></span>  
  
 <span data-ttu-id="a7091-213">RDL 式に新しい配列を作成するには、定義するクラスのメソッドで配列を作成し、そのクラスを許可一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="a7091-213">To create a new array in an RDL expression, create the array in a method on a class that you define, and add that class to the allow list.</span></span>  
  
 <span data-ttu-id="a7091-214">RDL 式に新しい配列を作成するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7091-214">To create a new array in an RDL expression, you must do the following:</span></span>  
  
-   <span data-ttu-id="a7091-215">新しいクラスを定義し、そのクラスのメソッドで配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a7091-215">Define a new class and create the array in a method on that class.</span></span>  
  
-   <span data-ttu-id="a7091-216">このクラスを許可一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="a7091-216">Add the class to the allow list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7091-217">参照</span><span class="sxs-lookup"><span data-stu-id="a7091-217">See Also</span></span>  
 <span data-ttu-id="a7091-218">[RSReportServer 構成ファイル](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="a7091-218">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 [<span data-ttu-id="a7091-219">Report Server Service Trace Log</span><span class="sxs-lookup"><span data-stu-id="a7091-219">Report Server Service Trace Log</span></span>](report-server/report-server-service-trace-log.md)  
  
  
