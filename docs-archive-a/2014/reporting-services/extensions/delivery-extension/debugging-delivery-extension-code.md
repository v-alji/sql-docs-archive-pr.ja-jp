---
title: 配信拡張機能のコードのデバッグ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb80ac97f5c0e346b208784f1fa5b857ff93ef57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741562"
---
# <a name="debugging-delivery-extension-code"></a><span data-ttu-id="b4f2c-102">配信拡張機能のコードのデバッグ</span><span class="sxs-lookup"><span data-stu-id="b4f2c-102">Debugging Delivery Extension Code</span></span>
  <span data-ttu-id="b4f2c-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] には、ご自分の配信拡張機能コードを分析してエラーを探すのに役立ついくつかのデバッグ ツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your delivery extension code and locate errors in it.</span></span> <span data-ttu-id="b4f2c-104">最適なデバッグ ツールは、使用する目的によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-104">The tool that works best will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="b4f2c-105">この例では、[!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-105">This example uses [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].</span></span>  
  
#### <a name="to-debug-your-delivery-extension-code"></a><span data-ttu-id="b4f2c-106">配信拡張機能のコードをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="b4f2c-106">To debug your delivery extension code</span></span>  
  
1.  <span data-ttu-id="b4f2c-107">[!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] を起動し、配信拡張機能のプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-107">Launch [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] and open your delivery extension project.</span></span>  
  
2.  <span data-ttu-id="b4f2c-108">プロジェクトをビルドし、配信拡張機能アセンブリとその .pdb ファイルをレポート サーバーとレポート マネージャーに配置します。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-108">Build the project and deploy your delivery extension assembly and the accompanying .pdb file to the report server and Report Manager.</span></span> <span data-ttu-id="b4f2c-109">配置の詳細については、「[配信拡張機能の配置](deploying-a-delivery-extension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-109">For more information about deployment, see [Deploying a Delivery Extension](deploying-a-delivery-extension.md).</span></span>  
  
3.  <span data-ttu-id="b4f2c-110">サブスクリプション ユーザー インターフェイスを記述してレポート マネージャーを拡張した場合は、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で配信拡張機能のコードを開いたまま、Internet Explorer を開いてレポート マネージャーに移動します。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-110">If you have written a subscription user interface to extend Report Manager, open Internet Explorer and navigate to Report Manager while leaving your delivery extension code open in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="b4f2c-111">レポート マネージャーのサブスクリプション ユーザー インターフェイスを配置していない場合は、クライアント アプリケーションを開き、そこから SOAP API を使用して配信拡張機能を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-111">If you do not have a subscription user interface deployed for Report Manager, simply open the client application from which you call your delivery extension using the SOAP API.</span></span>  
  
4.  <span data-ttu-id="b4f2c-112">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] および配信拡張機能のプロジェクトに移動し、コードにブレーク ポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-112">Navigate to [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and your delivery extension project, and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="b4f2c-113">配信拡張機能プロジェクトのウィンドウをアクティブにしたまま、 **[デバッグ]** メニューの **[プロセスにアタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-113">With the delivery extension project still the active window, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="b4f2c-114">**[プロセスにアタッチ]** ダイアログが開きます。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-114">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="b4f2c-115">プロセスの一覧から aspnet_wp.exe プロセス (アプリケーションを IIS 6.0 に配置している場合は w3wp.exe ) を選択し、 **[アタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-115">From the list of processes, select the aspnet_wp.exe process (or w3wp.exe if your application is deployed on IIS 6.0), and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="b4f2c-116">配信拡張機能を使用して新しいサブスクリプションを定義します。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-116">Define a new subscription using your delivery extension.</span></span> <span data-ttu-id="b4f2c-117">通常は、レポート マネージャーまたは SOAP API を使用します。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-117">You will most likely use Report Manager or the SOAP API.</span></span> <span data-ttu-id="b4f2c-118">これにより、デバッガーが呼び出され、ブレーク ポイントに対応するコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-118">This should invoke the debugger and execute code corresponding to your break points.</span></span>  
  
8.  <span data-ttu-id="b4f2c-119">**F11** キーを使用してコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-119">Step through your code using the **F11** key.</span></span> <span data-ttu-id="b4f2c-120">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用したデバッグの詳細については、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4f2c-120">For more information about using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] for debugging, see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f2c-121">参照</span><span class="sxs-lookup"><span data-stu-id="b4f2c-121">See Also</span></span>  
 <span data-ttu-id="b4f2c-122">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="b4f2c-122">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="b4f2c-123">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="b4f2c-123">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
