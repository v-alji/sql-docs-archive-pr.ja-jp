---
title: 'レッスン 4: プログラムによるレポート定義の更新 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1f0a1d46-6d6d-4f67-b51e-06dbbbffacf9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c090fc023e3ac47927b99ab61a45fd8ca2c79321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639830"
---
# <a name="lesson-4-update-the-report-definition-programmatically"></a><span data-ttu-id="f126b-102">レッスン 4 : プログラムによるレポート定義の更新</span><span class="sxs-lookup"><span data-stu-id="f126b-102">Lesson 4: Update the Report Definition Programmatically</span></span>
  <span data-ttu-id="f126b-103">前のレッスンでは、レポート サーバーからレポート定義を読み込み、レポート フィールドにその参照を指定しました。次は、レポート定義を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f126b-103">Now that the report definition has been loaded from the report server and you have a reference to it using the report field, you need to update the report definition.</span></span> <span data-ttu-id="f126b-104">この例では、レポートの `Description` プロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="f126b-104">For this example, you will update the `Description` property for the report.</span></span>  
  
### <a name="to-update-the-report-definition"></a><span data-ttu-id="f126b-105">レポート定義を更新するには</span><span class="sxs-lookup"><span data-stu-id="f126b-105">To update the report definition</span></span>  
  
1.  <span data-ttu-id="f126b-106">Program.cs ファイル (の場合は module1.vb) で UpdateReportDefinition () メソッドのコードを次の [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] コードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f126b-106">Replace the code for the UpdateReportDefinition() method in the Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void UpdateReportDefinition()  
    {  
        System.Console.WriteLine("Updating Report Definition");  
  
        // Create a list of the Items Choices for the Report. The   
        // ItemsChoiceType118 enum represents all the properties  
        // available in the report and the ItemsElementName   
        // represents the properties that exist in the current   
        // instance of the report.  
        List<ItemsChoiceType118> _reportItems =   
            new List<ItemsChoiceType118>(_report.ItemsElementName);  
  
        // Locate the index for the Description property  
        int index = _reportItems.IndexOf(  
            ItemsChoiceType118.Description);  
  
        // The Description item is of type StringLocIDType, so   
        // cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
  
        // Update the Description for the Report  
        ((StringLocIDType)_report.Items[index]).Value =   
            "New Report Description";  
  
        System.Console.WriteLine("- New Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
    }  
    ```  
  
    ```vb  
    Private Sub UpdateReportDefinition()  
  
        System.Console.WriteLine("Updating Report Definition")  
  
        'Create a list of the Items Choices for the Report. The   
        'ItemsChoiceType118 enum represents all the properties  
        'available in the report and the ItemsElementName   
        'represents the properties that exist in the current   
        'instance of the report.  
        Dim reportItems As List(Of ItemsChoiceType118) = _  
            New List(Of ItemsChoiceType118)(m_report.ItemsElementName)  
  
        'Locate the index for the Description property  
        Dim index As Integer = _  
            reportItems.IndexOf(ItemsChoiceType118.Description)  
  
        'The Description item is of type StringLocIDType, so   
        'cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
        'Update the Description for the Report  
        DirectCast(m_report.Items(index), StringLocIDType).Value = _  
            "New Report Description"  
  
        System.Console.WriteLine("- New Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="f126b-107">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="f126b-107">Next Lesson</span></span>  
 <span data-ttu-id="f126b-108">次のレッスンでは、更新したレポート定義をもう一度レポート サーバーに保存します。</span><span class="sxs-lookup"><span data-stu-id="f126b-108">In the next lesson, you will save the updated report definition back to the report server.</span></span> <span data-ttu-id="f126b-109">「[レッスン 5: レポート定義をレポートサーバーにパブリッシュする」を](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="f126b-109">See [Lesson 5: Publish the Report Definition to the Report Server](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f126b-110">参照</span><span class="sxs-lookup"><span data-stu-id="f126b-110">See Also</span></span>  
 [<span data-ttu-id="f126b-111">RDL スキーマから生成されたクラスを使用したレポートの更新 SSRS チュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="f126b-111">Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)  
  
  
