---
title: パッケージの保護レベルを設定または変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da8e63028498097b4321e4ef1383fbc8aa5845b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741126"
---
# <a name="set-or-change-the-protection-level-of-packages"></a><span data-ttu-id="5b4de-102">パッケージの保護レベルを設定または変更する</span><span class="sxs-lookup"><span data-stu-id="5b4de-102">Set or Change the Protection Level of Packages</span></span>
  <span data-ttu-id="5b4de-103">パッケージの内容やパッケージに含まれているパスワードなどの機密データへのアクセスを制御するには、`ProtectionLevel` プロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-103">To control access to the contents of packages and to the sensitive values that they contain, such as passwords, set the value of the `ProtectionLevel` property.</span></span> <span data-ttu-id="5b4de-104">プロジェクトをビルドするには、プロジェクトに含まれるパッケージの保護レベルがプロジェクトと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b4de-104">The packages contained in a project need to have the same protection level as the project, to build the project.</span></span> <span data-ttu-id="5b4de-105">`ProtectionLevel` プロパティ設定をプロジェクトで変更する場合は、パッケージのプロパティ設定を手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b4de-105">If you change the `ProtectionLevel` property setting on the project, you need to manually update the property setting for the packages.</span></span>  
  
 <span data-ttu-id="5b4de-106">パッケージ `ProtectionLevel` のライフサイクルのさまざまな段階でパッケージに適した設定を確認する方法については、「[パッケージ内の機密データの Access Control](security/access-control-for-sensitive-data-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b4de-106">For information about how to determine the `ProtectionLevel` settings that are appropriate for your packages at different stages in the package life cycle, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span> <span data-ttu-id="5b4de-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のセキュリティ機能の概要については、「[セキュリティの概要 #40; Integration Services & #41;](security/security-overview-integration-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b4de-107">For an overview of security features in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], see [Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md).</span></span>  
  
 <span data-ttu-id="5b4de-108">このトピックの手順では、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] または dtutil コマンド プロンプト ユーティリティを使用して `ProtectionLevel` プロパティを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-108">The procedures in this topic describe how to use either [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or the dtutil command prompt utility to change the `ProtectionLevel` property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b4de-109">このトピックの手順に加えて、通常、パッケージのインポートまたはエクスポート時にパッケージの `ProtectionLevel` プロパティを設定または変更できます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-109">In addition to the procedures in this topic, you can typically set or change the `ProtectionLevel` property of a package when you import or export the package.</span></span> <span data-ttu-id="5b4de-110">また、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを使用してパッケージを保存するときにも、パッケージの `ProtectionLevel` プロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-110">You can also change the `ProtectionLevel` property of a package when you use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard to save a package.</span></span>  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a><span data-ttu-id="5b4de-111">SQL Server データ ツールでパッケージの保護レベルを設定または変更するには</span><span class="sxs-lookup"><span data-stu-id="5b4de-111">To set or change the protection level of a package in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="5b4de-112">トピックのプロパティで使用可能な値を確認 `ProtectionLevel` し、パッケージ[の保護レベルを設定](security/access-control-for-sensitive-data-in-packages.md)して、パッケージの適切な値を決定します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-112">Review the available values for the `ProtectionLevel` property in the topic, [Setting the Protection Level of Packages](security/access-control-for-sensitive-data-in-packages.md), and determine the appropriate value for your package.</span></span>  
  
2.  <span data-ttu-id="5b4de-113">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package.</span></span>  
  
3.  <span data-ttu-id="5b4de-114">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-114">Open the package in the [!INCLUDE[ssIS](../includes/ssis-md.md)] designer.</span></span>  
  
4.  <span data-ttu-id="5b4de-115">[プロパティ] ウィンドウにパッケージのプロパティが表示されない場合は、デザイン画面をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b4de-115">If the Properties window does not show the properties of the package, click the design surface.</span></span>  
  
5.  <span data-ttu-id="5b4de-116">プロパティウィンドウの**セキュリティ**グループで、プロパティに適切な値を選択し `ProtectionLevel` ます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-116">In the Properties window, in the **Security** group, select the appropriate value for the `ProtectionLevel` property.</span></span>  
  
     <span data-ttu-id="5b4de-117">パスワードを必要とする保護レベルを選択する場合は、 **[PackagePassword]** プロパティの値としてパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-117">If you select a protection level that requires a password, enter the password as the value of the **PackagePassword** property.</span></span>  
  
6.  <span data-ttu-id="5b4de-118">**[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックして、変更したパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-118">On the **File** menu, select **Save Selected Items** to save the modified package.</span></span>  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a><span data-ttu-id="5b4de-119">コマンド プロンプトでパッケージの保護レベルを設定または変更するには</span><span class="sxs-lookup"><span data-stu-id="5b4de-119">To set or change the protection level of packages at the command prompt</span></span>  
  
1.  <span data-ttu-id="5b4de-120">トピックのプロパティで使用可能な値を確認 `ProtectionLevel` し、パッケージ[の保護レベルを設定](security/access-control-for-sensitive-data-in-packages.md)して、パッケージの適切な値を決定します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-120">Review the available values for the `ProtectionLevel` property in the topic, [Setting the Protection Level of Packages](security/access-control-for-sensitive-data-in-packages.md), and determine the appropriate value for your package.</span></span>  
  
2.  <span data-ttu-id="5b4de-121">トピック「dtutil ユーティリティ」のオプションのマッピングを確認 `Encrypt` し、選択したプロパティの値として使用する適切な整数を決定し[dtutil Utility](dtutil-utility.md) `ProtectionLevel` ます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-121">Review the mappings for the `Encrypt` option in the topic, [dtutil Utility](dtutil-utility.md), and determine the appropriate integer to use as the value of the selected `ProtectionLevel` property.</span></span>  
  
3.  <span data-ttu-id="5b4de-122">コマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-122">Open a Command Prompt window.</span></span>  
  
4.  <span data-ttu-id="5b4de-123">コマンド プロンプトで、`ProtectionLevel` プロパティを設定するパッケージが格納されているフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-123">At the command prompt, navigate to the folder that contains the package or packages for which you want to set the `ProtectionLevel` property.</span></span>  
  
     <span data-ttu-id="5b4de-124">次の手順に示す構文の例では、このフォルダーは現在のフォルダーであると想定しています。</span><span class="sxs-lookup"><span data-stu-id="5b4de-124">The syntax examples shown in the following step assume that this folder is the current folder.</span></span>  
  
5.  <span data-ttu-id="5b4de-125">次のいずれかの例のようなコマンドを使用して、パッケージの保護レベルを設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-125">Set or change the protection level of the package or packages by using a command similar to the one of the following examples:</span></span>  
  
    -   <span data-ttu-id="5b4de-126">次のコマンドでは、ファイル システム内の個々のパッケージの `ProtectionLevel` プロパティがレベル 2 の [機微なデータをパスワードで暗号化する] に設定され、パスワードが "strongpassword" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-126">The following command sets the `ProtectionLevel` property of an individual package in the file system to level 2, "Encrypt sensitive with password", with the password, "strongpassword":</span></span>  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   <span data-ttu-id="5b4de-127">次のコマンドでは、ファイル システム内の特定のフォルダーに存在するすべてのパッケージの `ProtectionLevel` プロパティがレベル 2 の [機微なデータをパスワードで暗号化する] に設定され、パスワードが "strongpassword" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5b4de-127">The following command sets the `ProtectionLevel` property of all packages in a particular folder in the file system to level 2, "Encrypt sensitive with password", with the password, "strongpassword":</span></span>  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         <span data-ttu-id="5b4de-128">バッチ ファイルで同様のコマンドを使用する場合は、ファイルのプレースホルダー「%f」をバッチ ファイルでは「%%f」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5b4de-128">If you use a similar command in a batch file, enter the file placeholder, "%f", as "%%f" in the batch file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b4de-129">参照</span><span class="sxs-lookup"><span data-stu-id="5b4de-129">See Also</span></span>  
 [<span data-ttu-id="5b4de-130">dtutil ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="5b4de-130">dtutil Utility</span></span>](dtutil-utility.md)  
  
  
