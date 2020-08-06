---
title: '[資格情報] ([データソースのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.credentials.f1
- "10100"
ms.assetid: 14c3eeb6-d37b-4fda-967b-43afcdb48119
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 491da16e6cd38db54c4d27bd8497ca7fdfaae5b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641509"
---
# <a name="data-source-properties-dialog-box-credentials"></a><span data-ttu-id="a8e31-102">[資格情報] ([データ ソースのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="a8e31-102">Data Source Properties Dialog Box, Credentials</span></span>
  <span data-ttu-id="a8e31-103">**[データ ソースのプロパティ]** ダイアログ ボックスの **[資格情報]** を選択すると、レポート内のデータ ソースに接続するための資格情報を表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="a8e31-103">Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to a data source in the report.</span></span> <span data-ttu-id="a8e31-104">指定した資格情報は、データ ソースへのアクセス、およびレポート プレビュー用のデータのコピーのキャッシュに使用されます。</span><span class="sxs-lookup"><span data-stu-id="a8e31-104">The credentials that you provide are used to access the data source and to cache a copy of the data for previewing reports.</span></span> <span data-ttu-id="a8e31-105">プレビュー データのキャッシュの方法の詳細については、「 [レポートのプレビュー](reports/previewing-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e31-105">For more information about how preview data is cached, see [Previewing Reports](reports/previewing-reports.md).</span></span> <span data-ttu-id="a8e31-106">資格情報の詳細については、「 [レポート データ ソースに関する資格情報と接続情報を指定する](report-data/specify-credential-and-connection-information-for-report-data-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e31-106">For more information about credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a8e31-107">Options</span><span class="sxs-lookup"><span data-stu-id="a8e31-107">Options</span></span>  
 <span data-ttu-id="a8e31-108">**[Windows 認証 (統合セキュリティ) を使用する]**</span><span class="sxs-lookup"><span data-stu-id="a8e31-108">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="a8e31-109">Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="a8e31-109">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="a8e31-110">**[次のユーザー名とパスワードを使用]**</span><span class="sxs-lookup"><span data-stu-id="a8e31-110">**Use this user name and password**</span></span>  
 <span data-ttu-id="a8e31-111">特定のユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e31-111">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="a8e31-112">共有データ ソースの場合、レポート サーバー プロジェクトをターゲット サーバーにパブリッシュするときに、データベース用の保存された資格情報としてユーザー名とパスワードが保存されます。</span><span class="sxs-lookup"><span data-stu-id="a8e31-112">For shared data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="a8e31-113">ユーザー名とパスワードを Windows 資格情報として使用する場合は、ターゲット サーバーにパブリッシュされた共有データ ソースのプロパティを編集できます。</span><span class="sxs-lookup"><span data-stu-id="a8e31-113">If you want to use the user name and password as Windows credentials, you can edit the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="a8e31-114">詳細については、「[共有データ ソースを作成、削除、または変更する &#40;レポート マネージャー&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e31-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).</span></span>  
  
 <span data-ttu-id="a8e31-115">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="a8e31-115">**User name**</span></span>  
 <span data-ttu-id="a8e31-116">データ ソースへのログインに使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="a8e31-116">Type a user name to log in to the data source.</span></span>  
  
 <span data-ttu-id="a8e31-117">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="a8e31-117">**Password**</span></span>  
 <span data-ttu-id="a8e31-118">データ ソースへのログインに使用するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="a8e31-118">Type a password to log in to the data source.</span></span>  
  
 <span data-ttu-id="a8e31-119">**資格情報を要求する**</span><span class="sxs-lookup"><span data-stu-id="a8e31-119">**Prompt for credentials**</span></span>  
 <span data-ttu-id="a8e31-120">レポートの実行時に資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="a8e31-120">Select this option to prompt for credentials when the report is run.</span></span>  
  
 <span data-ttu-id="a8e31-121">**[プロンプト文字列の入力]**</span><span class="sxs-lookup"><span data-stu-id="a8e31-121">**Enter prompt string**</span></span>  
 <span data-ttu-id="a8e31-122">データ ソースのログイン資格情報を指定するようユーザーに指示する文を入力します。</span><span class="sxs-lookup"><span data-stu-id="a8e31-122">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="a8e31-123">**資格情報がありません**</span><span class="sxs-lookup"><span data-stu-id="a8e31-123">**No credentials**</span></span>  
 <span data-ttu-id="a8e31-124">データ ソースの資格情報を指定しません。</span><span class="sxs-lookup"><span data-stu-id="a8e31-124">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="a8e31-125">このオプションは、データ ソースで資格情報が不要な場合、または他の方法で資格情報を渡している場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="a8e31-125">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e31-126">参照</span><span class="sxs-lookup"><span data-stu-id="a8e31-126">See Also</span></span>  
 <span data-ttu-id="a8e31-127">[[全般] ([データソースのプロパティ] ダイアログボックス)](../../2014/reporting-services/data-source-properties-dialog-box-general.md) </span><span class="sxs-lookup"><span data-stu-id="a8e31-127">[Data Source Properties Dialog Box, General](../../2014/reporting-services/data-source-properties-dialog-box-general.md) </span></span>  
 <span data-ttu-id="a8e31-128">[レポート データ ソースに関する資格情報と接続情報を指定する](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="a8e31-128">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 [<span data-ttu-id="a8e31-129">Reporting Services でのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="a8e31-129">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
