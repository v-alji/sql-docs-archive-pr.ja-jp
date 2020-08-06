---
title: '手順 3 : Directory プロパティの構成値の変更 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a71a7a181322d60caca98da4ddf3261cbce99c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633891"
---
# <a name="step-3-modifying-the-directory-property-configuration-value"></a><span data-ttu-id="03f01-102">手順 3:Directory プロパティの構成値の変更</span><span class="sxs-lookup"><span data-stu-id="03f01-102">Step 3: Modifying the Directory Property Configuration Value</span></span>
  <span data-ttu-id="03f01-103">ここでは、SSISTutorial.dtsConfig ファイルに保存されている構成設定のうち、パッケージ レベル変数 `User::varFolderName`の Value プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="03f01-103">In this task, you will modify the configuration setting, stored in the SSISTutorial.dtsConfig file, for the Value property of the package-level variable `User::varFolderName`.</span></span> <span data-ttu-id="03f01-104">この変数は、ForEach ループ コンテナーの Directory プロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="03f01-104">The variable updates the Directory property of the Foreach Loop container.</span></span> <span data-ttu-id="03f01-105">変更後の値は、 `New Sample Data` 前のタスクで作成したフォルダーを指します。</span><span class="sxs-lookup"><span data-stu-id="03f01-105">The modified value will point to the `New Sample Data` folder that you created in the previous task.</span></span> <span data-ttu-id="03f01-106">構成設定を変更し、パッケージを実行すると、パッケージ レベル変数によって Directory プロパティが更新されます。この更新では、パッケージにもともと構成されていた Directory 値は使用されず、構成ファイルから生成された値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="03f01-106">After you modify the configuration setting and run the package, the Directory property will be updated by the variable, using the value populated from the configuration file instead of the directory value originally configured in the package.</span></span>  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a><span data-ttu-id="03f01-107">Directory プロパティの構成設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="03f01-107">To modify the configuration setting of the Directory property</span></span>  
  
1.  <span data-ttu-id="03f01-108">前の実習でパッケージ構成ウィザードを使用して作成した SSISTutorial.dtsConfig 構成ファイルを探し、メモ帳などのテキスト エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="03f01-108">In Notepad or any other text editor, locate and open the SSISTutorial.dtsConfig configuration file that you created by using the Package Configuration Wizard in the previous task.</span></span>  
  
2.  <span data-ttu-id="03f01-109">**ConfiguredValue**要素の値を、 `New Sample Data` 前のタスクで作成したフォルダーのパスと一致するように変更します。</span><span class="sxs-lookup"><span data-stu-id="03f01-109">Change the value of the **ConfiguredValue** element to match the path of the `New Sample Data` folder that you created in the previous task.</span></span> <span data-ttu-id="03f01-110">パスは引用符で囲まないでください。</span><span class="sxs-lookup"><span data-stu-id="03f01-110">Do not surround the path in quotes.</span></span> <span data-ttu-id="03f01-111">`New Sample Data`フォルダーがドライブのルートレベルにある場合 (C: など \\ )、更新された XML は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="03f01-111">If the `New Sample Data` folder is at the root level of your drive (for example, C:\\), the updated XML should be similar to the following sample:</span></span>  
  
     `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
     <span data-ttu-id="03f01-112">もちろん、ファイルの見出し情報、、 `GeneratedBy` `GeneratedFromPackageID` 、および作成**日**は異なります。</span><span class="sxs-lookup"><span data-stu-id="03f01-112">The heading information, `GeneratedBy`, `GeneratedFromPackageID`, and **GeneratedDate** will be different in your file, of course.</span></span> <span data-ttu-id="03f01-113">`Configuration` 要素に注目してください。</span><span class="sxs-lookup"><span data-stu-id="03f01-113">The element to note is the `Configuration` element.</span></span> <span data-ttu-id="03f01-114">変数の `Value` プロパティである `User::varFolderName` に、C:\New Sample Data が含まれています。</span><span class="sxs-lookup"><span data-stu-id="03f01-114">The `Value` property of the variable, `User::varFolderName`, now contains C:\New Sample Data.</span></span>  
  
3.  <span data-ttu-id="03f01-115">変更を保存し、テキスト エディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="03f01-115">Save the change, and then close the text editor.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="03f01-116">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="03f01-116">Next Task in Lesson</span></span>  
 [<span data-ttu-id="03f01-117">手順 4:レッスン 5 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="03f01-117">Step 4: Testing the Lesson 5 Tutorial Package</span></span>](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
