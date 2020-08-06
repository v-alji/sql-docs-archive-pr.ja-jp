---
title: 'レッスン 3: レポートサーバーからのレポート定義の読み込み |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dc6ed26703599792b9c739f8d185ae4f190fc8be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639843"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a><span data-ttu-id="8c720-102">レッスン 3 : レポート サーバーからのレポート定義の読み込み</span><span class="sxs-lookup"><span data-stu-id="8c720-102">Lesson 3: Load a Report Definition from the Report Server</span></span>
  <span data-ttu-id="8c720-103">プロジェクトを作成し、RDL スキーマからクラスを生成すると、レポート定義をレポート サーバーから読み込めるようになります。</span><span class="sxs-lookup"><span data-stu-id="8c720-103">After you have created your project and generated the classes from the RDL schema, you are ready to load a report definition from the report server.</span></span>  
  
### <a name="to-load-a-report-definition"></a><span data-ttu-id="8c720-104">レポート定義を読み込むには</span><span class="sxs-lookup"><span data-stu-id="8c720-104">To load a report definition</span></span>  
  
1.  <span data-ttu-id="8c720-105">クラスの先頭にプライベートフィールド `ReportUpdater` (を使用している場合はモジュール) を追加し [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Report` ます。</span><span class="sxs-lookup"><span data-stu-id="8c720-105">Add a private field at the top of the `ReportUpdater` class (module if you are using [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) for the `Report` class.</span></span> <span data-ttu-id="8c720-106">このフィールドは、アプリケーションの動作中、レポート サーバーから読み込んだレポートへの参照を保持するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c720-106">This field will be used to maintain a reference to report that is loaded from the report server for the life of the application.</span></span>  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  <span data-ttu-id="8c720-107">Program.cs ファイル ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] では Module1.vb) で、`LoadReportDefinition()` メソッドのコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8c720-107">Replace the code for the `LoadReportDefinition()` method in the Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report definition   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report definition   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="8c720-108">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="8c720-108">Next Lesson</span></span>  
 <span data-ttu-id="8c720-109">次のレッスンでは、レポート サーバーから読み込んだレポート定義を更新するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="8c720-109">In the next lesson, you will write code to update the report definition that was loaded from the report server.</span></span> <span data-ttu-id="8c720-110">「[レッスン 4: プログラムによるレポート定義の更新」を](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c720-110">See [Lesson 4: Update the Report Definition Programmatically](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c720-111">参照</span><span class="sxs-lookup"><span data-stu-id="8c720-111">See Also</span></span>  
 <span data-ttu-id="8c720-112">[RDL スキーマから生成されたクラスを使用したレポートの更新 SSRS チュートリアル &#40;&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="8c720-112">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="8c720-113">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8c720-113">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
