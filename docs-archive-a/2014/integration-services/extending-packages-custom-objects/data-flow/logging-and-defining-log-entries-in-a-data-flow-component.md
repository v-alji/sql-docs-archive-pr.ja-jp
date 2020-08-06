---
title: データ フロー コンポーネントのログ エントリの記録と定義 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- logs [Integration Services], custom
- custom log entries [Integration Services]
- custom data flow components [Integration Services], logging
- data flow components [Integration Services], logging
ms.assetid: 2190dba9-59b5-480b-b8e9-21d5a54c5917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 14dfec71679bbe455ae8be5face98b776a80b9e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713321"
---
# <a name="logging-and-defining-log-entries-in-a-data-flow-component"></a><span data-ttu-id="86b29-102">データ フロー コンポーネントのログ エントリの記録と定義</span><span class="sxs-lookup"><span data-stu-id="86b29-102">Logging and Defining Log Entries in a Data Flow Component</span></span>
  <span data-ttu-id="86b29-103">カスタム データ フロー コンポーネントは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.PostLogMessage%2A> インターフェイスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> メソッドを使用して既存のログ エントリにメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="86b29-103">Custom data flow components can post messages to an existing log entry by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.PostLogMessage%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span> <span data-ttu-id="86b29-104"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A> メソッドまたは <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスの同様のメソッドを使用して、ユーザーに情報を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="86b29-104">They can also present information to the user by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A> method or similar methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span> <span data-ttu-id="86b29-105">ただし、この方法では追加のイベントの発生と処理によるオーバーヘッドが発生し、ユーザーにとって意味のあるメッセージの詳細情報メッセージをユーザーが取捨選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86b29-105">However, this approach incurs the overhead of raising and handling additional events, and forces the user to sift through verbose informational messages for the messages that may be of interest to them.</span></span> <span data-ttu-id="86b29-106">次に示す方法でカスタム ログ エントリを使用すると、明確にラベル付けされたカスタム ログ情報をコンポーネントのユーザーに提供できます。</span><span class="sxs-lookup"><span data-stu-id="86b29-106">You can use a custom log entry as described below to provide distinctly labeled custom log information to users of your component.</span></span>  
  
## <a name="registering-and-using-a-custom-log-entry"></a><span data-ttu-id="86b29-107">カスタム ログ エントリの登録と使用</span><span class="sxs-lookup"><span data-stu-id="86b29-107">Registering and Using a Custom Log Entry</span></span>  
  
### <a name="registering-a-custom-log-entry"></a><span data-ttu-id="86b29-108">カスタム ログ エントリの登録</span><span class="sxs-lookup"><span data-stu-id="86b29-108">Registering a Custom Log Entry</span></span>  
 <span data-ttu-id="86b29-109">コンポーネントで使用するためにカスタム ログ エントリを登録するには、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterLogEntries%2A> 基本クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="86b29-109">To register a custom log entry for use by your component, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterLogEntries%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class.</span></span> <span data-ttu-id="86b29-110">次の例では、カスタム ログ エントリを登録し、名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="86b29-110">The following example registers a custom log entry and provides a name and description.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Runtime;  
...  
private const string MyLogEntryName = "My Custom Component Log Entry";  
private const string MyLogEntryDescription = "Log entry from My Custom Component ";  
...  
    public override void RegisterLogEntries()  
    {  
      this.LogEntryInfos.Add(MyLogEntryName,  
        MyLogEntryDescription,  
        Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT);  
    }  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
...  
Private Const MyLogEntryName As String = "My Custom Component Log Entry"   
Private Const MyLogEntryDescription As String = "Log entry from My Custom Component "  
...  
Public  Overrides Sub RegisterLogEntries()   
  Me.LogEntryInfos.Add(MyLogEntryName, _  
    MyLogEntryDescription, _  
    Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT)   
End Sub  
```  
  
 <span data-ttu-id="86b29-111"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency> 列挙は、イベントのログが記録される頻度に関するヒントをランタイムに提供します。</span><span class="sxs-lookup"><span data-stu-id="86b29-111">The <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency> enumeration provides a hint to the runtime about how frequently the event will be logged:</span></span>  
  
-   <span data-ttu-id="86b29-112"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_OCCASIONAL> : 毎回実行時ではなく、不定期でイベントのログが記録されます。</span><span class="sxs-lookup"><span data-stu-id="86b29-112"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_OCCASIONAL>: Event is logged only sometimes, not during every execution.</span></span>  
  
-   <span data-ttu-id="86b29-113"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT> : 毎回実行時に一定の回数でイベントのログが記録されます。</span><span class="sxs-lookup"><span data-stu-id="86b29-113"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>: Event is logged a constant number of times during every execution.</span></span>  
  
-   <span data-ttu-id="86b29-114"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_PROPORTIONAL> : 完了した作業量に比例する回数だけイベントのログが記録されます。</span><span class="sxs-lookup"><span data-stu-id="86b29-114"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_PROPORTIONAL>: Event is logged a number of times proportional to the amount of work completed.</span></span>  
  
 <span data-ttu-id="86b29-115">上の例では、コンポーネントが実行ごとに 1 回エントリのログを記録するため、<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT> を使用します。</span><span class="sxs-lookup"><span data-stu-id="86b29-115">The example above uses <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT> because the component expects to log an entry once per execution.</span></span>  
  
 <span data-ttu-id="86b29-116">カスタム ログ エントリを登録し、カスタム コンポーネントのインスタンスをデータ フローのデザイナー画面に追加したら、デザイナーの **[ログ記録]** ダイアログ ボックスの使用可能なログ エントリの一覧に、"My Custom Component Log Entry" という名前の新しいログ エントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86b29-116">After registering the custom log entry and adding an instance of your custom component to the data flow designer surface, the **Logging** dialog box in the designer displays a new log entry with the name "My Custom Component Log Entry" in the list of available log entries.</span></span>  
  
### <a name="logging-to-a-custom-log-entry"></a><span data-ttu-id="86b29-117">カスタム ログ エントリへのログ記録</span><span class="sxs-lookup"><span data-stu-id="86b29-117">Logging to a Custom Log Entry</span></span>  
 <span data-ttu-id="86b29-118">カスタム ログ エントリを登録したら、コンポーネントがカスタム メッセージのログを記録できるようになります。</span><span class="sxs-lookup"><span data-stu-id="86b29-118">After registering the custom log entry, the component can now log custom messages.</span></span> <span data-ttu-id="86b29-119">次の例では、コンポーネントによって使用される SQL ステートメントのテキストを含む <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> メソッドの実行時にカスタム ログ エントリを記述します。</span><span class="sxs-lookup"><span data-stu-id="86b29-119">The example below writes a custom log entry during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method that contains the text of a SQL statement used by the component.</span></span>  
  
```csharp  
public override void PreExecute()  
{  
  DateTime now = DateTime.Now;  
  byte[] additionalData = null;  
  this.ComponentMetaData.PostLogMessage(MyLogEntryName,  
    this.ComponentMetaData.Name,  
    "Command Sent was: " + myCommand.CommandText,  
    now, now, 0, ref additionalData);  
}  
```  
  
```vb  
Public  Overrides Sub PreExecute()   
  Dim now As DateTime = DateTime.Now   
  Dim additionalData As Byte() = Nothing   
  Me.ComponentMetaData.PostLogMessage(MyLogEntryName, _  
    Me.ComponentMetaData.Name, _  
    "Command Sent was: " + myCommand.CommandText, _  
    now, now, 0, additionalData)   
End Sub  
```  
  
 <span data-ttu-id="86b29-120">ユーザーがパッケージを実行し、 **[ログ記録]** ダイアログ ボックスで [My Custom Component Log Entry] を選択すると、「User::My Custom Component Log Entry」というラベルが付けられたエントリがログに含まれます。</span><span class="sxs-lookup"><span data-stu-id="86b29-120">Now when the user executes the package, after selecting the "My Custom Component Log Entry" in the **Logging** dialog box, the log will contain an entry clearly labeled as "User::My Custom Component Log Entry."</span></span> <span data-ttu-id="86b29-121">この新しいログ エントリには、SQL ステートメントのテキスト、タイムスタンプ、および開発者によってログが記録された追加のデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="86b29-121">This new log entry contains the text of the SQL statement, the timestamp, and any additional data logged by the developer.</span></span>  
  
<span data-ttu-id="86b29-122">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="86b29-122">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="86b29-123">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86b29-123">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="86b29-124">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="86b29-124">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="86b29-125">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="86b29-125">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b29-126">参照</span><span class="sxs-lookup"><span data-stu-id="86b29-126">See Also</span></span>  
 [<span data-ttu-id="86b29-127">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="86b29-127">Integration Services &#40;SSIS&#41; Logging</span></span>](../../performance/integration-services-ssis-logging.md)  
  
  
