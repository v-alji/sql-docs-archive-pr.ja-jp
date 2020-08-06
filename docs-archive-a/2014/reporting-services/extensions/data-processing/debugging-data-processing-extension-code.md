---
title: データ処理拡張機能コードのデバッグ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bf7490145f91ee8b3cfc2357c34010bed593ed9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639901"
---
# <a name="debugging-data-processing-extension-code"></a><span data-ttu-id="04c0f-102">データ処理拡張機能コードのデバッグ</span><span class="sxs-lookup"><span data-stu-id="04c0f-102">Debugging Data Processing Extension Code</span></span>
  <span data-ttu-id="04c0f-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] には、ご自分のデータ処理拡張機能コードを分析してエラーを探すのに役立ついくつかのデバッグ ツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="04c0f-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your data processing extension code and locate errors in it.</span></span> <span data-ttu-id="04c0f-104">最適なデバッグ ツールは、使用する目的によって異なります。</span><span class="sxs-lookup"><span data-stu-id="04c0f-104">The tool that works best will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="04c0f-105">この例では、[!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="04c0f-105">This example uses [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].</span></span>  
  
#### <a name="to-debug-your-data-processing-extension-code"></a><span data-ttu-id="04c0f-106">データ処理拡張機能コードをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="04c0f-106">To debug your data processing extension code</span></span>  
  
1.  <span data-ttu-id="04c0f-107">[!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] を起動し、データ処理拡張機能プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="04c0f-107">Launch [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)], and open your data processing extension project.</span></span>  
  
2.  <span data-ttu-id="04c0f-108">プロジェクトを構築し、データ処理拡張機能アセンブリと付随する .pdb ファイルをレポート デザイナーに配置します。</span><span class="sxs-lookup"><span data-stu-id="04c0f-108">Build the project, and deploy your data processing extension assembly and the accompanying .pdb file to the Report Designer.</span></span> <span data-ttu-id="04c0f-109">配置の詳細については、「[データ処理拡張機能をレポート デザイナーに配置する方法](deploying-a-data-processing-extension-to-report-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04c0f-109">For more information about deployment, see [How to: Deploy a Data Processing Extension to Report Designer](deploying-a-data-processing-extension-to-report-designer.md).</span></span>  
  
3.  <span data-ttu-id="04c0f-110">データ処理拡張機能コードを [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で開いたまま、別の [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ウィンドウで新しいレポート プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="04c0f-110">Open a new Report Project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] while leaving your data processing extension code open in a separate window of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
4.  <span data-ttu-id="04c0f-111">データ処理拡張機能プロジェクトを含む [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のウィンドウに移動し、コードにブレーク ポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="04c0f-111">Navigate to the window of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] that contains your data processing extension project and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="04c0f-112">データ処理拡張機能プロジェクト ウィンドウを開いたまま、 **[デバッグ]** メニューの **[プロセスにアタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04c0f-112">With the data processing extension project window still active, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="04c0f-113">**[プロセスにアタッチ]** ダイアログが開きます。</span><span class="sxs-lookup"><span data-stu-id="04c0f-113">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="04c0f-114">プロセスの一覧から、レポート プロジェクトに対応する devenv.exe プロセスを選択して、 **[アタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04c0f-114">From the list of processes, select the devenv.exe process that corresponds to your Report Project and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="04c0f-115">レポート プロジェクトの **[レポート データ]** タブを使用して、レポート データ ソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="04c0f-115">Define your report data source using the **Report Data** tab of the Report Project.</span></span> <span data-ttu-id="04c0f-116">通常、汎用クエリ デザイナーを使用してカスタム データ ソースへのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="04c0f-116">You will most likely use the generic Query Designer to execute a query against your custom data source.</span></span> <span data-ttu-id="04c0f-117">これにより、デバッガーが呼び出され、ブレーク ポイントに対応するコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="04c0f-117">This should invoke the debugger and execute code corresponding to your break points.</span></span>  
  
8.  <span data-ttu-id="04c0f-118">F11 キーを使用してコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="04c0f-118">Step through your code using the F11 key.</span></span> <span data-ttu-id="04c0f-119">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用したデバッグの詳細については、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04c0f-119">For more information about using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] for debugging, see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c0f-120">参照</span><span class="sxs-lookup"><span data-stu-id="04c0f-120">See Also</span></span>  
 <span data-ttu-id="04c0f-121">[データ処理拡張機能の配置](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="04c0f-121">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="04c0f-122">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="04c0f-122">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="04c0f-123">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="04c0f-123">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="04c0f-124">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="04c0f-124">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
