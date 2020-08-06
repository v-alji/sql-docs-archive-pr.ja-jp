---
title: 'レッスン 5: レポート定義をレポートサーバーにパブリッシュする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 57fab70f-4a72-4413-a0ad-d0525caca3f7
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 54c2bad9f5b11e5ea72036fed9f60371ba9c593c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634170"
---
# <a name="lesson-5-publish-the-report-definition-to-the-report-server"></a>レッスン 5 : レポート サーバーへのレポート定義のパブリッシュ
  レポート定義を更新する最後の作業として、レポート定義をレポート サーバーにパブリッシュします。  
  
### <a name="to-publish-the-report-to-the-report-catalog"></a>レポートをレポート カタログにパブリッシュするには  
  
1.  `PublishReportDefinition()`Program.cs ファイル (の場合は module1.vb) で、メソッドのコードを次のコードに置き換え [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ます。  
  
    ```csharp  
    private void PublishReportDefinition()  
    {  
        System.Console.WriteLine("Publishing Report Definition");  
  
        string reportPath =  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        XmlSerializer serializer =  
            new XmlSerializer(typeof(Report));  
  
        using (MemoryStream stream = new MemoryStream())  
        {  
            // Serialize the report into the MemoryStream  
            serializer.Serialize(stream, _report);  
            stream.Position = 0;  
  
            byte[] bytes = stream.ToArray();  
  
            // Update the report on the report server  
            Warning[] warnings =   
                _reportService.SetItemDefinition(reportPath, bytes, null);  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub PublishReportDefinition()  
  
        System.Console.WriteLine("Publishing Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
        Dim serializer As XmlSerializer = _  
            New XmlSerializer(GetType(Report))  
  
        Using stream As MemoryStream = New MemoryStream  
  
            'Serialize the report into the MemoryStream  
            serializer.Serialize(stream, m_report)  
            stream.Position = 0  
  
            'Update the report on the report server  
            Dim bytes As Byte() = stream.ToArray  
            Dim warnings As Warning() = _  
                m_reportService.SetItemDefinition(reportPath, bytes, Nothing)  
  
        End Using  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>次のレッスン  
 次のレッスンでは、アプリケーションをコンパイルして実行し `SampleRDLSchema` ます。 「[レッスン 6: &#40;VB-C&#35;&#41;の RDL スキーマアプリケーションの実行](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [RDL スキーマから生成されたクラスを使用したレポートの更新 SSRS チュートリアル &#40;&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
