---
title: '[資格情報] ([データソースのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e47ba571e2b0adf2738499c1d027a4edde86e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642599"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a><span data-ttu-id="43249-102">[資格情報] ([データ ソースのプロパティ] ダイアログ ボックス) (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="43249-102">Data Source Properties Dialog Box, Credentials (Report Builder)</span></span>
  <span data-ttu-id="43249-103">**[データ ソースのプロパティ]** ダイアログ ボックスの **[資格情報]** を選択すると、レポート内の埋め込みデータ ソースに接続するための資格情報を表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="43249-103">Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to an embedded data source in the report.</span></span> <span data-ttu-id="43249-104">指定した資格情報は、レポートのプレビュー時、データ ソースにアクセスする際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="43249-104">The credentials that you provide are used to access the data source for previewing reports.</span></span> <span data-ttu-id="43249-105">詳細については、「 [レポート ビルダーでの資格情報の指定](../../2014/reporting-services/specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43249-105">For more information about credentials, see [Specify Credentials in Report Builder](../../2014/reporting-services/specify-credentials-in-report-builder.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="43249-106">Options</span><span class="sxs-lookup"><span data-stu-id="43249-106">Options</span></span>  
 <span data-ttu-id="43249-107">**[Windows 認証 (統合セキュリティ) を使用する]**</span><span class="sxs-lookup"><span data-stu-id="43249-107">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="43249-108">Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="43249-108">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="43249-109">**[次のユーザー名とパスワードを使用]**</span><span class="sxs-lookup"><span data-stu-id="43249-109">**Use this user name and password**</span></span>  
 <span data-ttu-id="43249-110">特定のユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="43249-110">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="43249-111">埋め込みデータ ソースの場合、レポート サーバー プロジェクトをターゲット サーバーにパブリッシュするときに、データベース用の保存された資格情報としてユーザー名とパスワードが保存されます。</span><span class="sxs-lookup"><span data-stu-id="43249-111">For embedded data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="43249-112">ユーザー名とパスワードを Windows 資格情報として使用する場合は、ターゲット サーバーにパブリッシュされた共有データ ソースのプロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="43249-112">If you want to use the user name and password as Windows credentials, you can change the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="43249-113">詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ドキュメントの「[共有データ ソースを作成、削除、または変更する (レポート マネージャー)](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43249-113">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) in the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="43249-114">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="43249-114">**User name**</span></span>  
 <span data-ttu-id="43249-115">データ ソースへのログオンに使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="43249-115">Type a user name to log on to the data source.</span></span>  
  
 <span data-ttu-id="43249-116">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="43249-116">**Password**</span></span>  
 <span data-ttu-id="43249-117">データ ソースへのログオンに使用するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="43249-117">Type a password to log on to the data source.</span></span>  
  
 <span data-ttu-id="43249-118">**資格情報を要求する**</span><span class="sxs-lookup"><span data-stu-id="43249-118">**Prompt for credentials**</span></span>  
 <span data-ttu-id="43249-119">レポートの実行時に資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="43249-119">Select this option to prompt for credentials when the report runs.</span></span>  
  
 <span data-ttu-id="43249-120">**[プロンプト文字列の入力]**</span><span class="sxs-lookup"><span data-stu-id="43249-120">**Enter prompt string**</span></span>  
 <span data-ttu-id="43249-121">データ ソースのログイン資格情報を指定するようユーザーに指示する文を入力します。</span><span class="sxs-lookup"><span data-stu-id="43249-121">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="43249-122">**資格情報がありません**</span><span class="sxs-lookup"><span data-stu-id="43249-122">**No credentials**</span></span>  
 <span data-ttu-id="43249-123">データ ソースの資格情報を指定しません。</span><span class="sxs-lookup"><span data-stu-id="43249-123">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="43249-124">このオプションは、データ ソースで資格情報が不要な場合、または他の方法で資格情報を渡している場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="43249-124">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
 <span data-ttu-id="43249-125">同じデータ拡張機能から、レポート サーバーで自動実行アカウントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43249-125">From some data extensions, the unattended execution account must be configured on the report server.</span></span>  
  
 <span data-ttu-id="43249-126">詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ドキュメントの「[外部データ ソースのデータを追加する (SSRS)](report-data/add-data-from-external-data-sources-ssrs.md)」および「[自動実行アカウントの構成 (SSRS 構成マネージャー)](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」で、対応するデータ ソースの種類に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="43249-126">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43249-127">参照</span><span class="sxs-lookup"><span data-stu-id="43249-127">See Also</span></span>  
 <span data-ttu-id="43249-128">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="43249-128">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="43249-129">[[データソースのプロパティ] ダイアログボックスの [全般 &#40;レポートビルダー&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="43249-129">[Data Source Properties Dialog Box, General &#40;Report Builder&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) </span></span>  
 <span data-ttu-id="43249-130">[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="43249-130">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="43249-131">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="43249-131">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
