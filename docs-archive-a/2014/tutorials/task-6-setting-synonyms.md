---
title: 'タスク 6: シノニムの設定 |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bde0c0ec7f230ba2325aa01328b191fd8fd67fa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631405"
---
# <a name="task-6-setting-synonyms"></a><span data-ttu-id="6bbcb-102">タスク 6: シノニムを設定する</span><span class="sxs-lookup"><span data-stu-id="6bbcb-102">Task 6: Setting Synonyms</span></span>
  <span data-ttu-id="6bbcb-103">このタスクでは、 **Country**ドメインの2つのドメイン値 ( **USA**と**米国**) を、**米国**を先頭の値としてシノニムとして設定します。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-103">In this task, you set two domain values, **USA** and **United States**, of the **Country** domain as synonyms with **United States** as the leading value.</span></span> <span data-ttu-id="6bbcb-104">**Country**ドメインの作成時に [**先頭の値を使用する**] オプションが選択されているため、 **country**ドメインの**米国**の値は**米国**として出力されます (米国は先頭の値になります)。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-104">Since the **Use Leading Values** option was selected when creating the **Country** domain, any **USA** values for the **Country** domain will be output as **United States** (as United States is the leading value).</span></span> <span data-ttu-id="6bbcb-105">詳細については、「[ドメイン値の変更](https://msdn.microsoft.com/library/hh510408.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-105">See [Change Domain Values](https://msdn.microsoft.com/library/hh510408.aspx) for more details.</span></span>

1.  <span data-ttu-id="6bbcb-106">ドメインの一覧から [ **Country** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-106">Select **Country** from the list of domains.</span></span>

2.  <span data-ttu-id="6bbcb-107">[**ドメイン値**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-107">Switch to the **Domain Values** tab.</span></span>

3.  <span data-ttu-id="6bbcb-108">ツールバーの [**新しいドメイン値の追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-108">Click **Add new domain value** button on the toolbar.</span></span>

4.  <span data-ttu-id="6bbcb-109">値に「 **USA** 」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-109">Type **USA** for the value and press **ENTER**.</span></span>

5.  <span data-ttu-id="6bbcb-110">CTRL キーまたは SHIFT キーを使用して**米国**と**USA**を複数選択するには、選択した項目を右クリックし、[**シノニムとして設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-110">Multiselect **United States** and **USA** using CTRL or SHIFT keys, right-click the selected items, and then click **Set as Synonyms**.</span></span> <span data-ttu-id="6bbcb-111">これらの値がグループ化されて、値の 1 つが先頭の値として指定され、その他の値がその値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-111">DQS groups these values and designate one of the values as the leading value that the other values are replaced with.</span></span>

     <span data-ttu-id="6bbcb-112">![[シノニムとして設定] メニュー](../../2014/tutorials/media/et-settingsynonyms-01.jpg "[シノニムとして設定] メニュー")</span><span class="sxs-lookup"><span data-stu-id="6bbcb-112">![Set as Synonyms Menu](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Set as Synonyms Menu")</span></span>

6.  <span data-ttu-id="6bbcb-113">**米国**が先頭の値として設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-113">Notice that **United States** is set as the leading value.</span></span> <span data-ttu-id="6bbcb-114">USA を先頭の値にする場合は、USA を右クリックし、[先頭に**設定**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-114">If you want USA to be the leading value, you can right-click on USA and select **Set as Leading** option.</span></span> <span data-ttu-id="6bbcb-115">このチュートリアルでは、**米国**を先頭の値として使用します。</span><span class="sxs-lookup"><span data-stu-id="6bbcb-115">For this tutorial, we use **United States** as the leading value.</span></span>

     <span data-ttu-id="6bbcb-116">![シノニムとしての米国と USA](../../2014/tutorials/media/et-settingsynonyms-02.jpg "シノニムとしての米国と USA")</span><span class="sxs-lookup"><span data-stu-id="6bbcb-116">![United States and USA as Synonyms](../../2014/tutorials/media/et-settingsynonyms-02.jpg "United States and USA as Synonyms")</span></span>

## <a name="next-step"></a><span data-ttu-id="6bbcb-117">次の手順</span><span class="sxs-lookup"><span data-stu-id="6bbcb-117">Next Step</span></span>
 [<span data-ttu-id="6bbcb-118">タスク 7: 複合ドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="6bbcb-118">Task 7: Creating a Composite Domain</span></span>](../../2014/tutorials/task-7-creating-a-composite-domain.md)


