---
title: 'レッスン 6: RDL スキーマアプリケーションの実行 (VB-C #) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2cd2386-2df8-4b69-ab81-9ad1a31f6d27
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5a0fc2cd9c12b4b1602f517dc215ca44e686c663
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711170"
---
# <a name="lesson-6-run-the-rdl-schema-application-vb-c"></a><span data-ttu-id="f00cc-102">レッスン 6: RDL スキーマアプリケーションの実行 (VB-C #)</span><span class="sxs-lookup"><span data-stu-id="f00cc-102">Lesson 6: Run the RDL Schema Application (VB-C#)</span></span>
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <span data-ttu-id="f00cc-103">には、統合開発環境 (IDE) からコンソール アプリケーションをビルドおよび実行する方法が 2 とおり用意されています。</span><span class="sxs-lookup"><span data-stu-id="f00cc-103">offers two methods to build and run a console application from the integrated development environment (IDE):</span></span>  
  
-   <span data-ttu-id="f00cc-104">開始 (デバッグあり)</span><span class="sxs-lookup"><span data-stu-id="f00cc-104">Start (with Debugging)</span></span>  
  
-   <span data-ttu-id="f00cc-105">デバッグなしで開始</span><span class="sxs-lookup"><span data-stu-id="f00cc-105">Start without Debugging</span></span>  
  
### <a name="to-build-and-run-the-samplerdlschema-application"></a><span data-ttu-id="f00cc-106">SampleRDLSchema アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="f00cc-106">To build and run the SampleRDLSchema application</span></span>  
  
1.  <span data-ttu-id="f00cc-107">[**デバッグ**] メニューから、[**デバッグなしで開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f00cc-107">From the **Debug** menu, click **Start Without Debugging**.</span></span> <span data-ttu-id="f00cc-108">この開始方法では、プログラムの実行が終了しても、コンソール ウィンドウが開いたままになります。</span><span class="sxs-lookup"><span data-stu-id="f00cc-108">This ensures that the console window remains open after the program has finished executing.</span></span>  
  
     <span data-ttu-id="f00cc-109">次のように、アプリケーションからコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="f00cc-109">The application prints the following output to the console:</span></span>  
  
    ```  
    Loading Report Definition  
    Updating Report Definition  
    - Old Description: <Old Report Description>  
    - New Description: <New Report Description>  
    Publishing Report Definition  
    ```  
  
2.  <span data-ttu-id="f00cc-110">コンソールを閉じるには、任意のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="f00cc-110">Press any key to close the console.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f00cc-111">エラーが発生すると、コンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="f00cc-111">Any errors that occur are written to the console.</span></span>  
  
3.  <span data-ttu-id="f00cc-112">サンプル アプリケーションの実行が終了すると、レポートの更新されたコピーがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="f00cc-112">When the sample application is finished running an updated copy of the report will be saved to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f00cc-113">参照</span><span class="sxs-lookup"><span data-stu-id="f00cc-113">See Also</span></span>  
 <span data-ttu-id="f00cc-114">[RDL スキーマから生成されたクラスを使用したレポートの更新 SSRS チュートリアル &#40;&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="f00cc-114">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="f00cc-115">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f00cc-115">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
