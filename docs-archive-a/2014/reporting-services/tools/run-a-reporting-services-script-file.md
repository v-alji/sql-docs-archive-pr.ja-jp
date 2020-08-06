---
title: Reporting Services スクリプト ファイルを実行する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c787d860838a57a2bd0f51aac1e9159833f038d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721002"
---
# <a name="run-a-reporting-services-script-file"></a><span data-ttu-id="82e2f-102">Reporting Services スクリプト ファイルを実行する</span><span class="sxs-lookup"><span data-stu-id="82e2f-102">Run a Reporting Services Script File</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="82e2f-103">スクリプト ファイルは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スクリプト環境 (RS.exe) を使用してコマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="82e2f-103">script files are run from the command prompt using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script environment (RS.exe).</span></span> <span data-ttu-id="82e2f-104">RS.exe には、ユーザーが使用できるコマンド プロンプト引数が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="82e2f-104">RS.exe has many command prompt arguments available for you to use.</span></span> <span data-ttu-id="82e2f-105">コマンド プロンプト オプションの詳細については、「[RS.exe ユーティリティ &#40;SSRS&#41;](rs-exe-utility-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82e2f-105">For more information about the command prompt options, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span> <span data-ttu-id="82e2f-106">他のスクリプトのサンプルについては、「 [SQL Server Reporting Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82e2f-106">For more script samples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="sample-command-lines"></a><span data-ttu-id="82e2f-107">コマンド ラインでの実行例</span><span class="sxs-lookup"><span data-stu-id="82e2f-107">Sample Command Lines</span></span>  
  
-   <span data-ttu-id="82e2f-108">スクリプト環境で Script.rss を次のように実行すると、ターゲット レポート サーバーが指定されます。</span><span class="sxs-lookup"><span data-stu-id="82e2f-108">Run Script.rss in the script environment designating the target report server.</span></span> <span data-ttu-id="82e2f-109">既定では、Windows 認証が適用されます。</span><span class="sxs-lookup"><span data-stu-id="82e2f-109">Windows Authentication is applied by default:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver  
    ```  
  
-   <span data-ttu-id="82e2f-110">スクリプト環境で Script.rss を次のように実行すると、Web サービスの呼び出しを認証するためのユーザー名とパスワードが指定されます。</span><span class="sxs-lookup"><span data-stu-id="82e2f-110">Run Script.rss in the script environment specifying a user name and password for authenticating the Web service calls:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   <span data-ttu-id="82e2f-111">スクリプト環境で Script.rss を次のように実行すると、30 秒のサーバー タイムアウトが指定されます。</span><span class="sxs-lookup"><span data-stu-id="82e2f-111">Run Script.rss in the script environment specifying a server time-out of 30 seconds:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   <span data-ttu-id="82e2f-112">スクリプト環境で Script.rss を次のように実行すると、 *report*と呼ばれるグローバル スクリプト変数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="82e2f-112">Run Script.rss in the script environment specifying a global script variable called *report*.</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   <span data-ttu-id="82e2f-113">スクリプト環境で Script.rss を次のように実行すると、スクリプト ファイルの Web サービス操作がバッチとして実行するように指定されます。</span><span class="sxs-lookup"><span data-stu-id="82e2f-113">Run Script.rss in the script environment specifying that the Web service operations in the script file are run as a batch.</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="82e2f-114">参照</span><span class="sxs-lookup"><span data-stu-id="82e2f-114">See Also</span></span>  
 [<span data-ttu-id="82e2f-115">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="82e2f-115">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
