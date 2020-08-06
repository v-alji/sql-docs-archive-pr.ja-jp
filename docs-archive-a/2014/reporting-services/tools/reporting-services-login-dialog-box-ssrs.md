---
title: '[Reporting Services ログイン] ダイアログ ボックス (SSRS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 232ee51614a668b07263c3e3a4182f23652135bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721039"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a><span data-ttu-id="76bb7-102">[Reporting Services ログイン] ダイアログ ボックス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="76bb7-102">Reporting Services Login Dialog Box (SSRS)</span></span>
  <span data-ttu-id="76bb7-103">**[Reporting Services ログイン]** ダイアログ ボックスを使用すると、レポートをレポート サーバーにパブリッシュする際に使用する資格情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="76bb7-103">Use the **Reporting Services Login** dialog box to provide credentials to publish reports to the report server.</span></span>  
  
-   <span data-ttu-id="76bb7-104">**メモ**プロジェクトの配置プロパティ**TargetServerURL**を設定してから初めてレポートをレポートサーバーにパブリッシュする場合は、指定したサーバー名がに類似していることを確認してください `http://localhost/reportserver` `http://localhost/reports` 。</span><span class="sxs-lookup"><span data-stu-id="76bb7-104">**Note** If this is the first time you have published a report to a report server since set you set the deployment property **TargetServerURL** for a project, verify that the server name you specified is similar to `http://localhost/reportserver`, and not `http://localhost/reports`.</span></span> <span data-ttu-id="76bb7-105">ローカル サーバーの `reports` ディレクトリではなく `reportserver` ディレクトリを指定すると、このダイアログ ボックスが間接的に開かれます。</span><span class="sxs-lookup"><span data-stu-id="76bb7-105">Specifying the `reports` directory on the local server instead of the `reportserver` directory indirectly causes this dialog box to open.</span></span> <span data-ttu-id="76bb7-106">**TargetServerURL** の設定の詳細については、「[配置プロパティを設定する &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76bb7-106">For more information about setting **TargetServerURL**, see [Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="76bb7-107">Options</span><span class="sxs-lookup"><span data-stu-id="76bb7-107">Options</span></span>  
 <span data-ttu-id="76bb7-108">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="76bb7-108">**Server**</span></span>  
 <span data-ttu-id="76bb7-109">レポート サーバーの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="76bb7-109">Displays the name of the report server.</span></span> <span data-ttu-id="76bb7-110">たとえば、「 `http://localhost/reportserver` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="76bb7-110">For example, `http://localhost/reportserver`.</span></span> <span data-ttu-id="76bb7-111">既定のポート 80 と異なるポートを使用するレポート サーバーの場合は、ポート番号を含めます。</span><span class="sxs-lookup"><span data-stu-id="76bb7-111">For report servers that use a different port than default port 80, include the port number.</span></span> <span data-ttu-id="76bb7-112">たとえば、「 `http://localhost:81/reportserver` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="76bb7-112">For example, `http://localhost:81/reportserver`.</span></span>  
  
 <span data-ttu-id="76bb7-113">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="76bb7-113">**User name**</span></span>  
 <span data-ttu-id="76bb7-114">Web サービスへのログインに使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="76bb7-114">Type the user name to log in to the Web service.</span></span>  
  
 <span data-ttu-id="76bb7-115">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="76bb7-115">**Password**</span></span>  
 <span data-ttu-id="76bb7-116">Web サービスへのログインに使用するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="76bb7-116">Type the password to log in to the Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76bb7-117">参照</span><span class="sxs-lookup"><span data-stu-id="76bb7-117">See Also</span></span>  
 <span data-ttu-id="76bb7-118">[Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="76bb7-118">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="76bb7-119">[レポートデータソースの資格情報と接続情報を指定する](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)[レポートデザイナー F1 ヘルプ](report-designer-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="76bb7-119">[Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Report Designer F1 Help](report-designer-f1-help.md)</span></span>  
  
  
