---
title: '手順 2: プロジェクトをプロジェクト配置モデルに変換する | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7b879b2bea4afd58a48cdfc6f0890353fe6758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632565"
---
# <a name="step-2-converting-the-project-to-the-project-deployment-model"></a><span data-ttu-id="11091-102">手順 2:プロジェクトをプロジェクト配置モデルに変換する</span><span class="sxs-lookup"><span data-stu-id="11091-102">Step 2: Converting the Project to the Project Deployment Model</span></span>
  <span data-ttu-id="11091-103">ここでは、Integration Services プロジェクトの変換ウィザードを使用して、プロジェクトをプロジェクト配置モデルに変換します。</span><span class="sxs-lookup"><span data-stu-id="11091-103">In this task, you will use the Integration Services Project Conversion Wizard to convert the project to the Project Deployment Model.</span></span>  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a><span data-ttu-id="11091-104">プロジェクトをプロジェクト配置モデルに変換する</span><span class="sxs-lookup"><span data-stu-id="11091-104">Converting the Project to the Project Deployment Model</span></span>  
  
1.  <span data-ttu-id="11091-105">[プロジェクト] メニューの [プロジェクト配置モデルに変換] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-105">On the Project Menu, click Convert to Project Deployment Model.</span></span>  
  
2.  <span data-ttu-id="11091-106">[Integration Services プロジェクトの変換ウィザードの概要] ページで、手順を確認して [次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-106">On the Integration Services Project Conversion Wizard Introduction page, review the steps then click Next.</span></span>  
  
3.  <span data-ttu-id="11091-107">[パッケージの選択] ページの [パッケージ] の一覧で、[Lesson 6.dtsx] を除くすべてのチェック ボックスをオフにし、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-107">On the Select Packages page, in the Packages list, clear all checkboxes except Lesson 6.dtsx then click Next.</span></span>  
  
4.  <span data-ttu-id="11091-108">[プロジェクトのプロパティの指定] ページで [次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-108">On the Specify Project Properties page, click Next.</span></span>  
  
5.  <span data-ttu-id="11091-109">[パッケージ実行タスクの更新] ページで [次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-109">On the Update Execute Package Task page click Next.</span></span>  
  
6.  <span data-ttu-id="11091-110">[構成の選択] ページで、[Lesson 6.dtsx] パッケージが構成の一覧で選択されていることを確認し、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-110">On the Select Configurations page, make sure the Lesson 6.dtsx package is selected in the Configurations list, then click Next.</span></span>  
  
7.  <span data-ttu-id="11091-111">[パラメーターの作成] ページの構成プロパティの一覧で、[Lesson 6.dtsx] パッケージが選択され、[スコープ] が [パッケージ] に設定されていることを確認し、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-111">On the Create Parameters page make sure the Lesson 6.dtsx package is selected, and the Scope is set to Package, in the Configuration Properties List, then Click Next.</span></span>  
  
8.  <span data-ttu-id="11091-112">[パラメーターの構成] ページで、[名前と値] の値が、レッスン 5 で変数と構成値に指定した名前および値と同じであることを確認し、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-112">On the Configure Parameters page verify that the values for Name and Value are the same name and value specified in Lesson 5 for the variable and configuration value, then click Next.</span></span>  
  
9. <span data-ttu-id="11091-113">[確認] ページの [概要] ウィンドウで、ウィザードは、構成ファイルの情報を使用して変換するプロパティを設定することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="11091-113">On the Review page, in the Summary pane, notice that the wizard has used the information from the configuration file to set the Properties to be converted.</span></span>  
  
10. <span data-ttu-id="11091-114">[変換] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-114">Click Convert.</span></span>  
  
     <span data-ttu-id="11091-115">変換が完了すると、プロジェクトが Visual Studio に保存されるまで変更が保存されないことを警告するメッセージ表示されます。</span><span class="sxs-lookup"><span data-stu-id="11091-115">When the conversion completes a message is displayed warning that the changes are not saved until the project is saved in Visual Studio.</span></span> <span data-ttu-id="11091-116">警告ダイアログで [OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-116">Click OK on the warning dialog.</span></span>  
  
11. <span data-ttu-id="11091-117">Integration Services プロジェクトの変換ウィザードで [閉じる] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11091-117">On the Integration Services Project Conversion Wizard click Close.</span></span>  
  
12. <span data-ttu-id="11091-118">SQL Server Data Tools で [ファイル] メニューをクリックし、[保存] をクリックして変換されたパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="11091-118">In SQL Server Data Tools, click the File menu, then click Save to save the converted package.</span></span>  
  
13. <span data-ttu-id="11091-119">[パラメーター] タブをクリックし、パッケージが VarFolderName のパラメーターに含まれ、値がレッスン 5 の構成ファイルの新しいサンプル データ フォルダーに指定されたパスと同じであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="11091-119">Click the Parameters Tab and verify that the package now contains a parameter for VarFolderName and that the value is the same path specified for the New Sample Data folder from the Lesson 5 configuration file.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="11091-120">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="11091-120">Next Task in Lesson</span></span>  
 [<span data-ttu-id="11091-121">手順 3:レッスン 6 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="11091-121">Step 3: Testing the Lesson 6 Package</span></span>](lesson-6-3-testing-the-lesson-6-package.md)  
  
  
