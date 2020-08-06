---
title: 'タスク 4: ドメインルールの設定 |Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42bdbd0228fdd3515f68ce830581f445242768e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632197"
---
# <a name="task-4-setting-domain-rules"></a><span data-ttu-id="72eb7-102">タスク 4: ドメイン ルールを設定する</span><span class="sxs-lookup"><span data-stu-id="72eb7-102">Task 4: Setting Domain Rules</span></span>
  <span data-ttu-id="72eb7-103">このタスクでは、**連絡先の電子メール**ドメインのルールを作成して、電子メールアドレスの末尾が\*\* \@ adventure-works.com\*\*であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="72eb7-103">In this task, you create a rule for the **Contact Email** domain to verify if the email address ends with **\@adventure-works.com**.</span></span> <span data-ttu-id="72eb7-104">ページの詳細については、「[ドメインルールの作成](https://msdn.microsoft.com/library/hh510397.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72eb7-104">See [Creating a Domain Rule](https://msdn.microsoft.com/library/hh510397.aspx) topic for more details on the page.</span></span>  
  
1.  <span data-ttu-id="72eb7-105">**ドメインリスト**の [**連絡先の電子メール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="72eb7-105">Click **Contact Email** in the **Domain list**.</span></span>  
  
2.  <span data-ttu-id="72eb7-106">右ペインの [**ドメインルール**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="72eb7-106">Switch to the **Domain Rules** tab in the right pane.</span></span>  
  
     <span data-ttu-id="72eb7-107">![[新しいドメイン ルールの追加] ツール バー ボタン](../../2014/tutorials/media/et-settingdomainrules-01.jpg "[新しいドメイン ルールの追加] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="72eb7-107">![Add a New Domain Rule Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Add a New Domain Rule Toolbar Button")</span></span>  
  
3.  <span data-ttu-id="72eb7-108">右側のウィンドウで、ツールバーの [**新しいドメインルールの追加**] ボタン (画像を参照) をクリックしてルールを追加します。</span><span class="sxs-lookup"><span data-stu-id="72eb7-108">In the right pane, click **Add a new domain rule** button on the toolbar (see the image) to add a rule.</span></span>  
  
4.  <span data-ttu-id="72eb7-109">**規則名**として「**電子メールの検証**」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="72eb7-109">Type **Email Validation** for the **rule name** and press **ENTER**.</span></span> <span data-ttu-id="72eb7-110">[**アクティブ**] チェックボックスは、既定でオンになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="72eb7-110">The **Active** check box should be checked by default.</span></span> <span data-ttu-id="72eb7-111">このコントロールを使用すると、ルールを一時的に非アクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="72eb7-111">This control allows you to deactivate a rule temporarily.</span></span>  
  
5.  <span data-ttu-id="72eb7-112">[**ルールの作成**] ペインで、**下矢印**をクリックし、[**値の末尾**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="72eb7-112">In the **Build a Rule** pane, click **down arrow**, and select **Value ends with**.</span></span>  
  
6.  <span data-ttu-id="72eb7-113">テキストボックスに「 \*\* \@ adventure-works.com\*\* 」と入力し、 **tab**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="72eb7-113">Type **\@adventure-works.com** in the text box and press **TAB**.</span></span> <span data-ttu-id="72eb7-114">[**ルールの作成**] ペインの [**選択した句に新しい条件を追加**] ツールバーボタンをクリックすると、さらに条件を追加できます。</span><span class="sxs-lookup"><span data-stu-id="72eb7-114">You can add more conditions by clicking **Add a new condition to the selected clause** toolbar button in the **Build a Rule** pane.</span></span>  
  
     <span data-ttu-id="72eb7-115">![電子メール検証ルール](../../2014/tutorials/media/et-settingdomainrules-02.jpg "電子メール検証ルール")</span><span class="sxs-lookup"><span data-stu-id="72eb7-115">![Email Validation Rule](../../2014/tutorials/media/et-settingdomainrules-02.jpg "Email Validation Rule")</span></span>  
  
7.  <span data-ttu-id="72eb7-116">サンプルデータに対してルールをテストするには、右側のペインのツールバーにある [**テストデータに対して選択したドメインルールを実行**する] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="72eb7-116">Click **Run the selected domain rule on test data** button on the toolbar in the right pane to test the rule against sample data.</span></span>  
  
     <span data-ttu-id="72eb7-117">![[テスト データについて選択したドメイン ルールを実行します] ツール バー ボタン](../../2014/tutorials/media/et-settingdomainrules-03.jpg "[テスト データについて選択したドメイン ルールを実行します] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="72eb7-117">![Run the Domain Rule on Test Data Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Run the Domain Rule on Test Data Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="72eb7-118">[**ドメインルールのテスト**] ダイアログボックスで、ツールバーの [**ドメインルールの新しいテスト用語を追加**します] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="72eb7-118">In the **Test Domain Rule** dialog box, click **Adds a new testing term for the domain rule** button on the toolbar.</span></span>  
  
     <span data-ttu-id="72eb7-119">![[ドメイン ルールのテスト] ダイアログ ボックス](../../2014/tutorials/media/et-settingdomainrules-04.jpg "[ドメイン ルールのテスト] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="72eb7-119">![Test Domain Rule Dialog Box](../../2014/tutorials/media/et-settingdomainrules-04.jpg "Test Domain Rule Dialog Box")</span></span>  
  
9. <span data-ttu-id="72eb7-120">[ **Contact Email** ] 列に「 **frank7 \@ adventure-works.com** (有効な値)」と入力します。</span><span class="sxs-lookup"><span data-stu-id="72eb7-120">Type **frank7\@adventure-works.com** (a valid value) in the **Contact Email** column.</span></span>  
  
10. <span data-ttu-id="72eb7-121">前の2つの手順を繰り返して、 **joe2 \@ adventure-work.com**を追加します (の値が無効な場合は、')。</span><span class="sxs-lookup"><span data-stu-id="72eb7-121">Repeat previous two steps to add **joe2\@adventure-work.com** (an invalid value with no 's').</span></span>  
  
11. <span data-ttu-id="72eb7-122">ツールバーの最後のボタン ([**すべての用語でドメインルールをテスト**]) をクリックして、ルールに対して入力データをテストします。</span><span class="sxs-lookup"><span data-stu-id="72eb7-122">Click the last button (**Test the domain rule on all the terms**) on the toolbar to test the input data against the rule.</span></span>  
  
     <span data-ttu-id="72eb7-123">![[すべての用語でドメイン ルールをテスト] ツール バー ボタン](../../2014/tutorials/media/et-settingdomainrules-05.jpg "[すべての用語でドメイン ルールをテスト] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="72eb7-123">![Test the Domain Rule on All Terms Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-05.jpg "Test the Domain Rule on All Terms Toolbar Button")</span></span>  
  
12. <span data-ttu-id="72eb7-124">最初のエントリが有効な項目として、2 番目のエントリが無効な項目として表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="72eb7-124">Notice that the first entry is shown as a valid item and the second one as an invalid item.</span></span>  
  
     <span data-ttu-id="72eb7-125">![ドメイン ルールのテストの結果](../../2014/tutorials/media/et-settingdomainrules-06.jpg "ドメイン ルールのテストの結果")</span><span class="sxs-lookup"><span data-stu-id="72eb7-125">![Test Domain Rule Results](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Test Domain Rule Results")</span></span>  
  
13. <span data-ttu-id="72eb7-126">[**閉じる**] をクリックして [**ドメインルールのテスト**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="72eb7-126">Click **Close** to close the **Test Domain Rule** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="72eb7-127">次の手順</span><span class="sxs-lookup"><span data-stu-id="72eb7-127">Next Step</span></span>  
 [<span data-ttu-id="72eb7-128">タスク 5: 用語ベースのリレーションを設定する</span><span class="sxs-lookup"><span data-stu-id="72eb7-128">Task 5: Setting Term Based Relationships</span></span>](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
