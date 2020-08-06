---
title: 'レッスン 9: アプリケーションをビルドして実行する | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 068deb075f0f60dde634ac29f6f8f934448dc6a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632963"
---
# <a name="lesson-9-build-and-run-the-application"></a><span data-ttu-id="da95f-102">レッスン 9: アプリケーションをビルドして実行する</span><span class="sxs-lookup"><span data-stu-id="da95f-102">Lesson 9: Build and Run the Application</span></span>
  <span data-ttu-id="da95f-103">データ テーブルのデータ フィルターを作成した後は、Web サイト アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="da95f-103">After you create a data filter for the data table, your next step is to build and run the website application.</span></span>

### <a name="to-build-and-run-the-application"></a><span data-ttu-id="da95f-104">アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="da95f-104">To build and run the application</span></span>

1.  <span data-ttu-id="da95f-105">**Ctrl キーを押しながら F5 キー** を押して Default.aspx ページをデバッグせずに実行するか、または F5 キーを押してページをデバッグしながら実行します。</span><span class="sxs-lookup"><span data-stu-id="da95f-105">Press **CTRL+F5** to run the Default.aspx page without debugging, or press F5 to run the page with debugging.</span></span>

     <span data-ttu-id="da95f-106">ビルド プロセスの一部としてレポートがコンパイルされます。検出されたエラー (レポートで使用されている式の構文エラーなど) は、Visual Studio ウィンドウの下部にある **[タスク一覧]** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="da95f-106">As part of the build process, the report is compiled and any errors found (such as a syntax error in an expression used in the report) are added to the **Task List** that is located at the bottom of the Visual Studio window.</span></span>

     <span data-ttu-id="da95f-107">Web ページがブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="da95f-107">The webpage appears in the browser.</span></span> <span data-ttu-id="da95f-108">ReportViewer コントロールにレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da95f-108">The ReportViewer control displays the report.</span></span> <span data-ttu-id="da95f-109">ツール バーを使用して、レポート内の移動、ズーム、およびレポートの Excel へのエクスポートを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="da95f-109">You can use the toolbar to browse through the report, zoom, and export the report to Excel.</span></span>

2.  <span data-ttu-id="da95f-110">**[名前]** 列の任意の行にマウス カーソルを合わせます。</span><span class="sxs-lookup"><span data-stu-id="da95f-110">Hover the mouse over any of the rows under **Name** column.</span></span> <span data-ttu-id="da95f-111">手の形のマウス カーソルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da95f-111">The mouse cursor will display a Hand symbol.</span></span>

3.  <span data-ttu-id="da95f-112">**[名前]** 列の値をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da95f-112">Click a value in the **Name** column.</span></span> <span data-ttu-id="da95f-113">対応するフィルター選択されたデータを含む子レポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="da95f-113">The child report is shown with the corresponding filtered data.</span></span>

4.  <span data-ttu-id="da95f-114">**ReportViewer**ツール バーの **[親レポートに戻る]** アイコンをクリックして、 **親** レポートに戻ります。</span><span class="sxs-lookup"><span data-stu-id="da95f-114">Click the icon, **Go back to parent report**, in the **ReportViewer** tool bar to navigate back to the **Parent** report.</span></span>

     <span data-ttu-id="da95f-115">![ReportViewer を使用した ssrs ドリルスルー](../../2014/tutorials/media/ssrs-drillthrough-report.png "ReportViewer を使用した ssrs ドリルスルー")</span><span class="sxs-lookup"><span data-stu-id="da95f-115">![ssrs drill through using ReportViewer](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs drill through using ReportViewer")</span></span>

5.  <span data-ttu-id="da95f-116">ブラウザーを閉じて終了します。</span><span class="sxs-lookup"><span data-stu-id="da95f-116">Close the browser to exit.</span></span>


