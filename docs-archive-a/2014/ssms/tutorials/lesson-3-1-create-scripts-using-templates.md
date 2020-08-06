---
title: テンプレートを使用したスクリプトの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b404ecc505e93c302e4c737f9c0b0161d9015519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717150"
---
# <a name="create-scripts-using-templates"></a><span data-ttu-id="08f79-102">テンプレートを使用したスクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="08f79-102">Create Scripts Using Templates</span></span>
  <span data-ttu-id="08f79-103">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、一般のさまざまな作業に適した [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがスクリプト テンプレートとして多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="08f79-103">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides a large number of script templates containing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for many common tasks.</span></span> <span data-ttu-id="08f79-104">これらのテンプレートには、テーブル名などのようなユーザーの入力した値に対応するパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="08f79-104">These templates contain parameters for the user-provided values such as a table name.</span></span> <span data-ttu-id="08f79-105">これらのパラメーターを使用して名前を一度入力すると、その名前は、スクリプト内の必要なすべての場所に自動的にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="08f79-105">Using the parameters, you can type the name once and then automatically copy the name to all the necessary locations within the script.</span></span> <span data-ttu-id="08f79-106">独自のカスタム テンプレートを作成し、頻繁に記述するスクリプトに役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="08f79-106">You can write your own custom templates to support the scripts that you write most often.</span></span> <span data-ttu-id="08f79-107">さらに、テンプレートの移動、またはテンプレートを保存する新規フォルダーの作成を行い、テンプレート ツリーを整理できます。</span><span class="sxs-lookup"><span data-stu-id="08f79-107">You can also reorganize the template tree, moving templates or creating new folders to hold the templates.</span></span> <span data-ttu-id="08f79-108">次の実習では、照合テンプレートを指定しつつ、テンプレートを使用してデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="08f79-108">In the following practice, you will use a template to create a database, specifying collation template.</span></span>  
  
## <a name="using-templates"></a><span data-ttu-id="08f79-109">テンプレートの使用</span><span class="sxs-lookup"><span data-stu-id="08f79-109">Using Templates</span></span>  
  
#### <a name="to-create-a-script-using-a-template"></a><span data-ttu-id="08f79-110">テンプレートを使用してスクリプトを作成するには</span><span class="sxs-lookup"><span data-stu-id="08f79-110">To create a script using a template</span></span>  
  
1.  <span data-ttu-id="08f79-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f79-111">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="08f79-112">テンプレート エクスプローラーではテンプレートがグループ別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="08f79-112">The templates in Template Explorer are organized into groups.</span></span> <span data-ttu-id="08f79-113">**[Database]** を展開し、 **[Create Database]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f79-113">Expand **Database**, and then double-click **Create Database**.</span></span>  
  
3.  <span data-ttu-id="08f79-114">**[データベース エンジンへの接続]** ダイアログ ボックスで接続情報を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f79-114">In the **Connect to Database Engine** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="08f79-115">新しいクエリ エディター ウィンドウが開き、 **Create Database** テンプレートの内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="08f79-115">A new Query Editor window opens, containing the contents of the **Create Database** template.</span></span>  
  
4.  <span data-ttu-id="08f79-116">**[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f79-116">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
5.  <span data-ttu-id="08f79-117">**[テンプレート パラメーターの値の指定]** ダイアログ ボックスの **[値]** 列には、 **Database_Name** パラメーターの推奨値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="08f79-117">In the **Specify Values for Template Parameters** dialog box, the **Value** column contains a suggested value for the **Database_Name** parameter.</span></span> <span data-ttu-id="08f79-118">**Database Name** パラメーターの [値] 列のボックスに「 **Marketing**」と入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f79-118">In the **Database Name** parameter box, type **Marketing**, and then click **OK**.</span></span> <span data-ttu-id="08f79-119">スクリプトの複数の場所に "Marketing" が挿入されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="08f79-119">Note how "Marketing" is inserted into the script in several locations.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="08f79-120">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="08f79-120">Next Task in Lesson</span></span>  
 [<span data-ttu-id="08f79-121">カスタム テンプレートの作成</span><span class="sxs-lookup"><span data-stu-id="08f79-121">Create Custom Templates</span></span>](lesson-3-2-create-custom-templates.md)  
  
  
