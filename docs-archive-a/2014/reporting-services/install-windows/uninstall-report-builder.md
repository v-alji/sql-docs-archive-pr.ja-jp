---
title: レポートビルダーのスタンドアロンバージョンをアンインストールする (レポートビルダー) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cda13248d1aa14ee3d57a951872d3ad8ded17da9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643705"
---
# <a name="uninstall-the-stand-alone-version-of-report-builder-report-builder"></a><span data-ttu-id="ad7af-102">スタンドアロン バージョンのレポート ビルダーのアンインストール (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="ad7af-102">Uninstall the Stand-Alone Version of Report Builder (Report Builder)</span></span>
  <span data-ttu-id="ad7af-103">スタンドアロン バージョンのレポート ビルダーは、コントロール パネルまたはコマンド ラインからアンインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-103">You can uninstall the stand-alone version of Report Builder from the control panel or the command line.</span></span> <span data-ttu-id="ad7af-104">[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンのレポート ビルダーをアンインストールするには、[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] をアンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad7af-104">You cannot uninstall the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version of Report Builder without uninstalling [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="ad7af-105">レポート ビルダーをコマンド ラインからアンインストールする場合に使用する構文は、/i オプションの代わりに /x オプションを使用する以外はレポート ビルダーをインストールする場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="ad7af-105">Uninstalling Report Builder from the command line uses syntax that is identical to the syntax you use to install Report Builder, except you use the /x option instead of the /i option.</span></span> <span data-ttu-id="ad7af-106">/quiet オプションやその他の標準のオプションも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-106">Command lines for uninstalling can also include the /quiet option and other standard options.</span></span> <span data-ttu-id="ad7af-107">レポート ビルダーの Windows インストーラー パッケージ (ReportBuilder3_x86.msi) を削除してしまった場合は、コマンド ラインを使用してレポート ビルダーをアンインストールするのは容易ではありません。</span><span class="sxs-lookup"><span data-stu-id="ad7af-107">If the Report Builder Windows Installer Package (ReportBuilder3_x86.msi) has been removed, you cannot use the command line easily to uninstall Report Builder.</span></span> <span data-ttu-id="ad7af-108">GUID を使用してレポート ビルダーを削除する方法の詳細については、MSDN ライブラリの msiexec プログラムのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad7af-108">To learn more about how you might be able to remove Report Builder by using its GUID, see the documentation for the msiexec program in the msdn library.</span></span>  
  
 <span data-ttu-id="ad7af-109">レポート ビルダーで使用しているフォルダーにカスタム ファイルが含まれている場合は、レポート ビルダーを削除しても、それらのフォルダーとファイルは削除されません。</span><span class="sxs-lookup"><span data-stu-id="ad7af-109">If folders used by Report Builder include custom files, the folders and the files are preserved when Report Builder is removed.</span></span> <span data-ttu-id="ad7af-110">レポート ビルダーのファイルのみが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-110">Only the Report Builder files are removed.</span></span>  
  
### <a name="to-uninstall-report-builder-from-the-control-panel"></a><span data-ttu-id="ad7af-111">レポート ビルダーをコントロール パネルからアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="ad7af-111">To uninstall Report Builder from the control panel</span></span>  
  
1.  <span data-ttu-id="ad7af-112">**[スタート]** ボタンをクリックし、 **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad7af-112">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="ad7af-113">コントロール パネルで、 **[プログラムと機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad7af-113">In the Control Panel, click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="ad7af-114">**[名前]** の一覧で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート ビルダーを見つけてクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad7af-114">Locate [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Builder in the **Name** list and click it.</span></span>  
  
4.  <span data-ttu-id="ad7af-115">[**アンインストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad7af-115">Click **Uninstall**.</span></span>  
  
5.  <span data-ttu-id="ad7af-116">レポート ビルダーをアンインストールするかどうかを確認するメッセージが表示された場合は、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad7af-116">If prompted to confirm the uninstall of Report Builder, click **Yes**.</span></span>  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a><span data-ttu-id="ad7af-117">レポート ビルダーをコマンド ラインからアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="ad7af-117">To uninstall Report Builder from the command line</span></span>  
  
1.  <span data-ttu-id="ad7af-118">**[スタート]** メニューの **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad7af-118">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="ad7af-119">[**名前**] ボックスに「」と入力します。`cmd.`</span><span class="sxs-lookup"><span data-stu-id="ad7af-119">In the **Open** text box, type `cmd.`</span></span>  
  
3.  <span data-ttu-id="ad7af-120">コマンド プロンプト ウィンドウで、ReportBuilder3_x86.msi が格納されているフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="ad7af-120">In the command prompt window, navigate to the folder with ReportBuilder3_x86.msi.</span></span>  
  
4.  <span data-ttu-id="ad7af-121">コマンド ラインに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="ad7af-121">Type a basic command line such as the following:</span></span>  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 <span data-ttu-id="ad7af-122">ログ記録を使用できる場合は、次のようなコマンド ラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad7af-122">If you can to include logging, use a command line such as the following:</span></span>  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
1.  <span data-ttu-id="ad7af-123">**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ad7af-123">Press **Enter**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7af-124">参照</span><span class="sxs-lookup"><span data-stu-id="ad7af-124">See Also</span></span>  
 <span data-ttu-id="ad7af-125">[インストール、アンインストール、およびレポートビルダーサポート](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="ad7af-125">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="ad7af-126">レポートビルダー &#40;レポートビルダーのスタンドアロンバージョンをインストール&#41;</span><span class="sxs-lookup"><span data-stu-id="ad7af-126">Install the Stand-Alone Version of Report Builder &#40;Report Builder&#41;</span></span>](install-report-builder.md)  
  
  
