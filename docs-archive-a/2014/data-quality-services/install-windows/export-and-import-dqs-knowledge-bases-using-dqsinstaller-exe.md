---
title: DQSInstaller.exe を使用した DQS ナレッジ ベースのエクスポートとインポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8234c63b-a018-4e55-8184-9a6bdf03274d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 64a8feb7bfded742da7563642b07181166fcbeab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736787"
---
# <a name="export-and-import-dqs-knowledge-bases-using-dqsinstallerexe"></a><span data-ttu-id="010b3-102">DQSInstaller.exe を使用した DQS ナレッジ ベースのエクスポートとインポート</span><span class="sxs-lookup"><span data-stu-id="010b3-102">Export and Import DQS Knowledge Bases Using DQSInstaller.exe</span></span>
  <span data-ttu-id="010b3-103">DQS の既存のインストールでは、コマンド プロンプトで DQSInstaller.exe ファイルを実行して、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のすべてのナレッジ ベースを DQS バックアップ ファイル (.dqsb) へ一度にエクスポートし、その後で .dqsb ファイルを使用してすべてのナレッジ ベースを別の [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] へ一度にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="010b3-103">For an existing installation of DQS, you can export all the knowledge bases in your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb) at once, and then later use the .dqsb file to import all the knowledge bases to a different [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="010b3-104">コマンド プロンプトからの DQSInstaller.exe の実行の詳細については、「 [コマンド プロンプトから DQSInstaller.exe を実行する](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) 」の「 [Data Quality Server のインストールを完了するための DQSInstaller.exe の実行](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="010b3-104">For more information about running DQSInstaller.exe from the command prompt, see [Run DQSInstaller.exe from Command Prompt](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) in [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
 <span data-ttu-id="010b3-105">この機能を使用すると、 *を使用して各ナレッジ ベースを .dqs ファイルへ個別にエクスポートすることなく、* の [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] すべての [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]ナレッジ ベースを一度にバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="010b3-105">This feature enables you to take a backup of *all* your knowledge bases in [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once without having to individually export each knowledge base to a .dqs file by using [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="010b3-106">同様に、 *を使用して .dqs ファイルから各ナレッジ ベースを個別にインポートすることなく、* すべての [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ナレッジ ベースをバックアップ ファイルから別の [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]へ一度にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="010b3-106">Similarly, you can import *all* the knowledge bases from the backup file into another [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once without having to individually import each knowledge base from a .dqs file by using [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="010b3-107">これは、コンピューターの [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] をアンインストールして別のコンピューターに再インストールするときにナレッジ ベースをバックアップして復元する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="010b3-107">This is particularly useful for backing up and restoring your knowledge bases when you are uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] on a computer, and then reinstalling it on a different computer.</span></span> <span data-ttu-id="010b3-108">既存の [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] インストールのすべてのナレッジ ベースを DQS バックアップ ファイル (.dqsb) へエクスポートし、別のコンピューターに [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] をインストールした後にすべてのナレッジ ベースをバックアップ ファイルからインポートすることが簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="010b3-108">You can easily export all the knowledge bases in an existing installation of [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb), and then import all the knowledge bases from the backup file after installing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] on a different computer.</span></span>  
  
##  <a name="exporting-knowledge-bases-to-dqsb-file"></a><a name="export"></a><span data-ttu-id="010b3-109">ナレッジベースの dqsb ファイルへのエクスポート</span><span class="sxs-lookup"><span data-stu-id="010b3-109">Exporting Knowledge Bases to .dqsb File</span></span>  
 <span data-ttu-id="010b3-110">既存の [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のすべてのナレッジ ベースをいつでもエクスポートできます。また、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]のアンインストール中にエクスポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="010b3-110">You can export all the knowledge bases in the existing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at any time or while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].</span></span>  
  
-   <span data-ttu-id="010b3-111">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のすべてのナレッジ ベースを DQS バックアップ ファイル (.dqsb) へエクスポートするには、コマンド プロンプトで `exportkbs` パラメーターとナレッジ ベースのエクスポート先の完全パスおよびファイル名を指定して DQSInstaller.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="010b3-111">To export all the knowledge bases in a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb), run DQSInstaller.exe with the `exportkbs` parameter from the command prompt, along with the full path and file name where you want to export the knowledge bases.</span></span> <span data-ttu-id="010b3-112">たとえば、すべてのナレッジ ベースを C: ドライブの DQSBackup.dqsb ファイルへエクスポートするには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="010b3-112">For example, to export all the knowledge bases to the DQSBackup.dqsb file in the C: drive:</span></span>  
  
    ```  
    dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="010b3-113">指定したファイル名が指定した場所に既に存在する場合は、ファイルを上書きするかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="010b3-113">If the provided file name already exists at the specified location, the installer prompts you whether to overwrite the file.</span></span>  
  
-   <span data-ttu-id="010b3-114">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]のアンインストール中にすべてのナレッジ ベースを DQS バックアップ ファイルへエクスポートするには、コマンド プロンプトで `uninstall` パラメーターとナレッジ ベースのエクスポート先の完全パスおよびファイル名を指定して DQSInstaller.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="010b3-114">To export all the knowledge bases to a DQS backup file while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], run DQSInstaller.exe with the `uninstall` parameter from the command prompt, along with the full path and file name where you want to export the knowledge bases.</span></span> <span data-ttu-id="010b3-115">たとえば、すべてのナレッジ ベースを C: ドライブの DQSBackup.dqsb ファイルへエクスポートしてから [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]をアンインストールするには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="010b3-115">For example, to export all the knowledge bases to the DQSBackup.dqsb file in the C: drive, and then uninstall [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]:</span></span>  
  
    ```  
    dqsinstaller.exe -uninstall c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="010b3-116">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] パラメーターを使用してコマンド プロンプトから `uninstall` をアンインストールするときに DQS バックアップ ファイルの完全パスとファイル名を指定しなかった場合は、すべてのナレッジ ベースが削除されることを示すメッセージが表示され、アンインストール プロセスを続行するかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="010b3-116">If you do not specify the full path and file name of the DQS backup file while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] from the command prompt using the `uninstall` parameter, a message is displayed stating that all the knowledge bases will be deleted, and allows you to choose whether to continue with the uninstall process.</span></span>  
  
##  <a name="importing-knowledge-bases-from-dqsb-file"></a><a name="import"></a><span data-ttu-id="010b3-117">Dqsb ファイルからのナレッジベースのインポート</span><span class="sxs-lookup"><span data-stu-id="010b3-117">Importing Knowledge Bases from .dqsb File</span></span>  
 <span data-ttu-id="010b3-118">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のインストールが完了した後にすべてのナレッジ ベースを DQS バックアップ ファイル (.dqsb) からインポートできます。</span><span class="sxs-lookup"><span data-stu-id="010b3-118">You can import all the knowledge bases from a DQS backup file (.dqsb) after completing the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation.</span></span> <span data-ttu-id="010b3-119">ナレッジベースをインポートするには、有効な DQS バックアップ ファイル (.dqsb) が必要です。</span><span class="sxs-lookup"><span data-stu-id="010b3-119">To import knowledge bases, you must have a valid DQS backup file (.dqsb).</span></span>  
  
 <span data-ttu-id="010b3-120">コマンド プロンプトで `importkbs` パラメーターとナレッジ ベースのインポート元の完全パスおよびファイル名を指定して DQSInstaller.exe ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="010b3-120">Run the DQSInstaller.exe file with the `importkbs` parameter from the command prompt, along with the full path and file name from where you want to import the knowledge bases.</span></span> <span data-ttu-id="010b3-121">たとえば、すべてのナレッジ ベースを C: ドライブの DQSBackup.dqsb ファイルからインポートするには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="010b3-121">For example, to import all the knowledge bases from the DQSBackup.dqsb file in the C: drive:</span></span>  
  
```  
dqsinstaller.exe -importkbs c:\DQSBackup.dqsb  
```  
  
 <span data-ttu-id="010b3-122">インポートしているナレッジ ベースと同じ名前のナレッジ ベースが [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] に既に存在する場合は、インポートされたナレッジ ベースの名前の後にアンダースコア (_) と 1 から始まる整数値が付加されます。</span><span class="sxs-lookup"><span data-stu-id="010b3-122">If there are existing knowledge bases in your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] with the same name as the ones you are importing, the names of the imported knowledge bases will be appended with an underscore (_) followed by an integer value starting with 1.</span></span> <span data-ttu-id="010b3-123">たとえば、"CompanyName" ドメインが重複する場合、インポートされたドメイン名は "CompanyName_1" になります。</span><span class="sxs-lookup"><span data-stu-id="010b3-123">For example, if the "CompanyName" domain is duplicate, the imported domain name will be "CompanyName_1."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="010b3-124">参照</span><span class="sxs-lookup"><span data-stu-id="010b3-124">See Also</span></span>  
 <span data-ttu-id="010b3-125">[Data Quality Server のインストールを完了するために DQSInstaller.exe を実行する](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="010b3-125">[Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md) </span></span>  
 <span data-ttu-id="010b3-126">[Data Quality Services のインストール](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="010b3-126">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 <span data-ttu-id="010b3-127">[ナレッジベースを dqs ファイルにエクスポートする](../export-a-knowledge-base-to-a-dqs-file.md) </span><span class="sxs-lookup"><span data-stu-id="010b3-127">[Export a Knowledge Base to a .dqs File](../export-a-knowledge-base-to-a-dqs-file.md) </span></span>  
 [<span data-ttu-id="010b3-128">.dqs ファイルからのナレッジ ベースのインポート</span><span class="sxs-lookup"><span data-stu-id="010b3-128">Import a Knowledge Base from a .dqs File</span></span>](../import-a-knowledge-base-from-a-dqs-file.md)  
  
  
