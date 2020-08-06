---
title: '[全般] ページ |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59073ac29f95f1e64bd0a9382366e9539ce1408a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632592"
---
# <a name="general-page"></a><span data-ttu-id="527cc-102">[全般] ページ</span><span class="sxs-lookup"><span data-stu-id="527cc-102">General Page</span></span>
  <span data-ttu-id="527cc-103">**[オプション]** ダイアログ ボックスの **[Integration Services デザイナー]** ページにある **[全般]** ページを使用すると、パッケージの読み込み、表示、およびアップグレードに関するオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="527cc-103">Use the **General** page of the **Integration Services Designers** page in the **Options** dialog box to specify the options for loading, displaying, and upgrading packages.</span></span>  
  
 <span data-ttu-id="527cc-104">**[全般]** ページを開くには、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[ツール]** メニューの **[オプション]** をクリックし、 **[ビジネス インテリジェンス デザイナー]** を展開して **[Integration Services デザイナー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="527cc-104">To open the **General** page, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Tools** menu, click **Options**, expand **Business Intelligence Designers**, and select **Integration Services Designers**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="527cc-105">オプション</span><span class="sxs-lookup"><span data-stu-id="527cc-105">Options</span></span>  
 <span data-ttu-id="527cc-106">**[パッケージの読み込み時にデジタル署名を確認する]**</span><span class="sxs-lookup"><span data-stu-id="527cc-106">**Check digital signature when loading a package**</span></span>  
 <span data-ttu-id="527cc-107">パッケージの読み込み時に [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でデジタル署名を確認する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="527cc-107">Select to have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] check the digital signature when loading a package.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="527cc-108">では、デジタル署名が存在するか、有効であるか、信頼されるソースから来たものであるかということだけが確認されます。</span><span class="sxs-lookup"><span data-stu-id="527cc-108">will only check whether the digital signature is present, is valid, and is from a trusted source.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="527cc-109">では、パッケージの署名後にパッケージが変更されたかどうかは確認されません。</span><span class="sxs-lookup"><span data-stu-id="527cc-109">will not check whether the package has been changed since the package was signed.</span></span>  
  
 <span data-ttu-id="527cc-110">**BlockedSignatureStates** レジストリ値を設定すると、このレジストリ値が、 **[パッケージの読み込み時にデジタル署名を確認する]** オプションをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="527cc-110">If you set the **BlockedSignatureStates** registry value, this registry value overrides the **Check digital signature when loading a package** option.</span></span> <span data-ttu-id="527cc-111">詳細については、「 [レジストリ値を設定して署名ポリシーを実装する](implement-a-signing-policy-by-setting-a-registry-value.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="527cc-111">For more information, see [Implement a Signing Policy by Setting a Registry Value](implement-a-signing-policy-by-setting-a-registry-value.md).</span></span>  
  
 <span data-ttu-id="527cc-112">詳細については、「 [デジタル署名を使用してパッケージのソースを特定する](security/identify-the-source-of-packages-with-digital-signatures.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="527cc-112">For more information about digital certificates and packages, see [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
 <span data-ttu-id="527cc-113">**[パッケージが署名されていない場合、警告を表示する]**</span><span class="sxs-lookup"><span data-stu-id="527cc-113">**Show warning if package is unsigned**</span></span>  
 <span data-ttu-id="527cc-114">署名されていないパッケージが読み込まれたときに、警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="527cc-114">Select to display a warning when loading a package that is not signed.</span></span>  
  
 <span data-ttu-id="527cc-115">**[優先順位制約ラベルを表示する]**</span><span class="sxs-lookup"><span data-stu-id="527cc-115">**Show precedence constraint labels**</span></span>  
 <span data-ttu-id="527cc-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] でパッケージを表示する場合に、優先順位制約でどのラベル ([成功]、[失敗]、または [完了]) を表示するかを選択します。</span><span class="sxs-lookup"><span data-stu-id="527cc-116">Select which label-Success, Failure, or Completion-to display on precedence constraints when viewing packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="527cc-117">**[スクリプト言語]**</span><span class="sxs-lookup"><span data-stu-id="527cc-117">**Scripting language**</span></span>  
 <span data-ttu-id="527cc-118">新しいスクリプト タスクおよびスクリプト コンポーネントの既定のスクリプト言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="527cc-118">Select the default scripting language for new Script tasks and Script components.</span></span>  
  
 <span data-ttu-id="527cc-119">**[接続文字列を更新して新しいプロバイダー名を使用する]**</span><span class="sxs-lookup"><span data-stu-id="527cc-119">**Update connection strings to use new provider names**</span></span>  
 <span data-ttu-id="527cc-120">[!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] パッケージを開くかアップグレードするときに、現在のリリースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]について、次のプロバイダーの名前を使用するように接続文字列を更新します。</span><span class="sxs-lookup"><span data-stu-id="527cc-120">When opening or upgrading [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] packages, update connection strings to use the names for the following providers, for the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="527cc-121">OLE DB プロバイダー</span><span class="sxs-lookup"><span data-stu-id="527cc-121">OLE DB provider</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="527cc-122">Native Client</span><span class="sxs-lookup"><span data-stu-id="527cc-122">Native Client</span></span>  
  
 <span data-ttu-id="527cc-123">[!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、接続マネージャーに格納されている接続文字列だけを更新します。</span><span class="sxs-lookup"><span data-stu-id="527cc-123">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers.</span></span> <span data-ttu-id="527cc-124">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の式言語またはスクリプト タスクのコードによって動的に構築される接続文字列は更新しません。</span><span class="sxs-lookup"><span data-stu-id="527cc-124">The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] expression language, or by using code in a Script task.</span></span>  
  
 <span data-ttu-id="527cc-125">**[新しいパッケージ ID の作成]**</span><span class="sxs-lookup"><span data-stu-id="527cc-125">**Create new package ID**</span></span>  
 <span data-ttu-id="527cc-126">[!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] パッケージをアップグレードするとき、アップグレードされたバージョンのパッケージ用に新しいパッケージ ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="527cc-126">When upgrading [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] packages, create new package IDs for the upgraded versions of the packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527cc-127">参照</span><span class="sxs-lookup"><span data-stu-id="527cc-127">See Also</span></span>  
 <span data-ttu-id="527cc-128">[セキュリティの概要 &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="527cc-128">[Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span></span>  
 [<span data-ttu-id="527cc-129">スクリプトによるパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="527cc-129">Extending Packages with Scripting</span></span>](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
