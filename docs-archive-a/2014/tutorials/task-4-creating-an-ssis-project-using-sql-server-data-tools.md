---
title: 'タスク 4: SQL Server Data Tools | を使用して SSIS プロジェクトを作成するMicrosoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 07976dbd2c84b1385d79ce3f4ce4f616e0f706b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717049"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a><span data-ttu-id="96dbb-102">タスク 4: SQL Server Data Tools を使用して SSIS プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="96dbb-102">Task 4: Creating an SSIS Project using SQL Server Data Tools</span></span>
  <span data-ttu-id="96dbb-103">このタスクでは、 **SQL Server Data Tools**を使用して、クレンジングを自動化し、仕入先データを照合することにより、SSIS プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="96dbb-103">In this task, you create an SSIS project by using **SQL Server Data Tools** to automate cleansing and matching supplier data.</span></span>

1.  <span data-ttu-id="96dbb-104">**SQL Server Data Tools**を起動します。</span><span class="sxs-lookup"><span data-stu-id="96dbb-104">Launch **SQL Server Data Tools**.</span></span> <span data-ttu-id="96dbb-105">[スタート] をクリックし、[**すべてのプログラム**]、[ **Microsoft SQL Server 2012**] の順にポイントし、[ **SQL Server Data Tools**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96dbb-105">Click Start, point to **All Programs**, expand **Microsoft SQL Server 2012**, and click **SQL Server Data Tools**.</span></span>

2.  <span data-ttu-id="96dbb-106">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96dbb-106">On the **File** menu, point to **New**, and click **Project**.</span></span>

3.  <span data-ttu-id="96dbb-107">[**インストールされたテンプレート**] ペインで [**ビジネスインテリジェンス**] を展開し、[ **Integration Services**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="96dbb-107">Expand **Business Intelligence** in the **Installed Templates** pane, and select **Integration Services**.</span></span>

     <span data-ttu-id="96dbb-108">![Visual Studio - [新しいプロジェクト] ダイアログ ボックス](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - [新しいプロジェクト] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="96dbb-108">![Visual Studio - New Project Dialog Box](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - New Project Dialog Box")</span></span>

4.  <span data-ttu-id="96dbb-109">**プロジェクトの種類の一覧**で [ **Integration Services プロジェクト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="96dbb-109">Select **Integration Services Project** in the **list of project types**.</span></span>

5.  <span data-ttu-id="96dbb-110">[**名前**] に「 **CleanseAndCurateSuppliers** 」と入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96dbb-110">Type **CleanseAndCurateSuppliers** for **Name** and click **OK**.</span></span>

6.  <span data-ttu-id="96dbb-111">**ソリューションエクスプローラー**ウィンドウで、 **.dtsx**を右クリックし、[**名前の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="96dbb-111">In **Solution Explorer** window, right-click **Package.dtsx** and select **Rename**.</span></span> <span data-ttu-id="96dbb-112">**ソリューションエクスプローラー**ウィンドウが表示されない場合は、メニューバーの [**表示**] をクリックし、[**ソリューションエクスプローラー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96dbb-112">If you don't see **Solution Explorer** window, click **View** on the menu bar and click **Solution Explorer**.</span></span>

     <span data-ttu-id="96dbb-113">![Package.dtsx - [名前の変更] メニュー](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - [名前の変更] メニュー")</span><span class="sxs-lookup"><span data-stu-id="96dbb-113">![Package.dtsx - Rename Menu](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - Rename Menu")</span></span>

7.  <span data-ttu-id="96dbb-114">「 **.Dtsx** 」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="96dbb-114">Type **CleanseAndCurate.dtsx** and press **ENTER**.</span></span> <span data-ttu-id="96dbb-115">**拡張子**が **.dtsx**のままであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="96dbb-115">Make sure that the **extension** remains **.dtsx**.</span></span>

## <a name="next-step"></a><span data-ttu-id="96dbb-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="96dbb-116">Next Step</span></span>
 [<span data-ttu-id="96dbb-117">タスク 5: データ フロー タスクを追加する</span><span class="sxs-lookup"><span data-stu-id="96dbb-117">Task 5: Adding Data Flow Task</span></span>](task-5-adding-data-flow-task.md)


