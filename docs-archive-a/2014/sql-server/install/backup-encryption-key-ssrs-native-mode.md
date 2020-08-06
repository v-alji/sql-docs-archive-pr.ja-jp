---
title: 暗号化キーのバックアップ (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d82a9b594e4a7ef7ceeb6737932e7e42a7f6fb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640490"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a><span data-ttu-id="47a2f-102">暗号化キーをバックアップする (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="47a2f-102">Backup Encryption Key (SSRS Native Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="47a2f-103">では、暗号化キーを使用して、レポート サーバー データベースに格納されている機密データのセキュリティを保護します。</span><span class="sxs-lookup"><span data-stu-id="47a2f-103">uses an encryption key to secure sensitive data that is stored in the report server database.</span></span> <span data-ttu-id="47a2f-104">このキーのバックアップを取ることは、暗号化された接続文字列と資格情報に継続してアクセスできるようにするうえで不可欠です。</span><span class="sxs-lookup"><span data-stu-id="47a2f-104">Having a backup of this key is essential for ensuring continued access to encrypted connection strings and credentials.</span></span> <span data-ttu-id="47a2f-105">レポート サーバー データベースを別のコンピューターに移動する場合や、レポート サーバー サービス アカウントのユーザー名またはパスワードを変更する場合は、このキーのバックアップ コピーを取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a2f-105">You must have a backup copy of this key if you move the report server database to another computer or if you change the user name or password of the Report Server service account.</span></span> <span data-ttu-id="47a2f-106">どちらの操作でも、前もって作成したバックアップ コピーからキーを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a2f-106">Both operations require that you restore the key from a backup copy that you previously created.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="47a2f-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="47a2f-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="47a2f-108">[暗号化キーのバックアップ] ダイアログ ボックスを開くには、 **構成マネージャーのナビゲーション ウィンドウで** [暗号化キー] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をクリックし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47a2f-108">To open the Backup Encryption Key dialog box, click **Encryption Keys** in the navigation pane of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, and then click **Backup**.</span></span> <span data-ttu-id="47a2f-109">このダイアログ ボックスは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーの [サービス アカウント] ページを使用してサービス アカウントを更新した場合にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="47a2f-109">This dialog box also appears when you update the service account using the Service Account page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="47a2f-110">Configuration Manager の詳細につい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ては、「 [Reporting Services Configuration Manager &#40;ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47a2f-110">For more information on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="47a2f-111">Options</span><span class="sxs-lookup"><span data-stu-id="47a2f-111">Options</span></span>  
 <span data-ttu-id="47a2f-112">**ファイルの場所**</span><span class="sxs-lookup"><span data-stu-id="47a2f-112">**File Location**</span></span>  
 <span data-ttu-id="47a2f-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して対称キーのファイル名と場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="47a2f-113">Specify a file name and location for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to the symmetric key.</span></span> <span data-ttu-id="47a2f-114">対称キーはプレーン テキストのまま保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="47a2f-114">The symmetric key is never stored in plain text.</span></span> <span data-ttu-id="47a2f-115">パスワードを入力してファイルを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a2f-115">You must type a password to protect the file.</span></span>  
  
 <span data-ttu-id="47a2f-116">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="47a2f-116">**Password**</span></span>  
 <span data-ttu-id="47a2f-117">ファイルを不正アクセスから保護するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="47a2f-117">Type a password that protects the file against unauthorized access.</span></span> <span data-ttu-id="47a2f-118">パスワードを知っているユーザーのみが、ファイル内にロックされているキーを復元できます。</span><span class="sxs-lookup"><span data-stu-id="47a2f-118">Only users who know the password will be able to restore the key that is locked inside the file.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="47a2f-119">では、強力なパスワード ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="47a2f-119">enforces a strong password policy.</span></span> <span data-ttu-id="47a2f-120">パスワードは 8 文字以上で、大文字と小文字、英数字、および 1 つ以上の記号文字の組み合わせにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a2f-120">The password must be at least 8 characters and include a combination of uppercase and lowercase alphanumeric characters and at least one symbol character.</span></span>  
  
 <span data-ttu-id="47a2f-121">**パスワードの確認入力**</span><span class="sxs-lookup"><span data-stu-id="47a2f-121">**Confirm Password**</span></span>  
 <span data-ttu-id="47a2f-122">入力したパスワードを再入力します。</span><span class="sxs-lookup"><span data-stu-id="47a2f-122">Re-type the password you entered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a2f-123">参照</span><span class="sxs-lookup"><span data-stu-id="47a2f-123">See Also</span></span>  
 <span data-ttu-id="47a2f-124">[Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="47a2f-124">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="47a2f-125">[Reporting Services の暗号化キーのバックアップと復元](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="47a2f-125">[Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="47a2f-126">[暗号化キーの削除と再作成  &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="47a2f-126">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="47a2f-127">[レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="47a2f-127">[Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span></span>  
 <span data-ttu-id="47a2f-128">[暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="47a2f-128">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 [<span data-ttu-id="47a2f-129">SSRS ネイティブモードの暗号化キー &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="47a2f-129">Encryption Keys &#40;SSRS Native Mode&#41;</span></span>](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
