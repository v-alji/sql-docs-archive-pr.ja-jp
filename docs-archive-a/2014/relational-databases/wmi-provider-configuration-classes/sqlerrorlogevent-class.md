---
title: SqlErrorLogEvent クラス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 358b6906e422be2984f2ebdbde636ad0b8376993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639923"
---
# <a name="sqlerrorlogevent-class"></a><span data-ttu-id="589a9-102">SqlErrorLogEvent クラス</span><span class="sxs-lookup"><span data-stu-id="589a9-102">SqlErrorLogEvent Class</span></span>
  <span data-ttu-id="589a9-103">指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイル内のイベントの表示に関するプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="589a9-103">Provides properties for viewing events in a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="589a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="589a9-104">Syntax</span></span>  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a><span data-ttu-id="589a9-105">Properties</span><span class="sxs-lookup"><span data-stu-id="589a9-105">Properties</span></span>  
 <span data-ttu-id="589a9-106">SQLErrorLogEvent クラスは、次のプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="589a9-106">The SQLErrorLogEvent class defines the following properties.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="589a9-107">FileName</span><span class="sxs-lookup"><span data-stu-id="589a9-107">FileName</span></span>|<span data-ttu-id="589a9-108">データ型: `string`</span><span class="sxs-lookup"><span data-stu-id="589a9-108">Data type: `string`</span></span><br /><br /> <span data-ttu-id="589a9-109">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="589a9-109">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="589a9-110">エラー ログ ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="589a9-110">The name of the error log file.</span></span>|  
|<span data-ttu-id="589a9-111">InstanceName</span><span class="sxs-lookup"><span data-stu-id="589a9-111">InstanceName</span></span>|<span data-ttu-id="589a9-112">データ型: `string`</span><span class="sxs-lookup"><span data-stu-id="589a9-112">Data type: `string`</span></span><br /><br /> <span data-ttu-id="589a9-113">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="589a9-113">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="589a9-114">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="589a9-114">Qualifiers: Key</span></span><br /><br /> <span data-ttu-id="589a9-115">ログ ファイルが存在する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="589a9-115">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the log file resides.</span></span>|  
|<span data-ttu-id="589a9-116">LogDate</span><span class="sxs-lookup"><span data-stu-id="589a9-116">LogDate</span></span>|<span data-ttu-id="589a9-117">データ型: `datetime`</span><span class="sxs-lookup"><span data-stu-id="589a9-117">Data type: `datetime`</span></span><br /><br /> <span data-ttu-id="589a9-118">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="589a9-118">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="589a9-119">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="589a9-119">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="589a9-120">イベントがログ ファイルに記録された日時。</span><span class="sxs-lookup"><span data-stu-id="589a9-120">The date and time that the event was recorded in the log file.</span></span>|  
|<span data-ttu-id="589a9-121">Message</span><span class="sxs-lookup"><span data-stu-id="589a9-121">Message</span></span>|<span data-ttu-id="589a9-122">データ型: `string`</span><span class="sxs-lookup"><span data-stu-id="589a9-122">Data type: `string`</span></span><br /><br /> <span data-ttu-id="589a9-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="589a9-123">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="589a9-124">イベント メッセージ。</span><span class="sxs-lookup"><span data-stu-id="589a9-124">The event message.</span></span>|  
|<span data-ttu-id="589a9-125">ProcessInfo</span><span class="sxs-lookup"><span data-stu-id="589a9-125">ProcessInfo</span></span>|<span data-ttu-id="589a9-126">データ型: `string`</span><span class="sxs-lookup"><span data-stu-id="589a9-126">Data type: `string`</span></span><br /><br /> <span data-ttu-id="589a9-127">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="589a9-127">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="589a9-128">イベントのソース サーバー プロセス ID (SPID) に関する情報。</span><span class="sxs-lookup"><span data-stu-id="589a9-128">Information about the source server process ID (SPID) for the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="589a9-129">解説</span><span class="sxs-lookup"><span data-stu-id="589a9-129">Remarks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="589a9-130">MOF</span><span class="sxs-lookup"><span data-stu-id="589a9-130">MOF</span></span>|<span data-ttu-id="589a9-131">Sqlmgmproviderxpsp2up.mof</span><span class="sxs-lookup"><span data-stu-id="589a9-131">Sqlmgmproviderxpsp2up.mof</span></span>|  
|<span data-ttu-id="589a9-132">[DLL]</span><span class="sxs-lookup"><span data-stu-id="589a9-132">DLL</span></span>|<span data-ttu-id="589a9-133">Sqlmgmprovider.dll</span><span class="sxs-lookup"><span data-stu-id="589a9-133">Sqlmgmprovider.dll</span></span>|  
|<span data-ttu-id="589a9-134">名前空間</span><span class="sxs-lookup"><span data-stu-id="589a9-134">Namespace</span></span>|<span data-ttu-id="589a9-135">\root\Microsoft\SqlServer\ComputerManagement10</span><span class="sxs-lookup"><span data-stu-id="589a9-135">\root\Microsoft\SqlServer\ComputerManagement10</span></span>|  
  
## <a name="example"></a><span data-ttu-id="589a9-136">例</span><span class="sxs-lookup"><span data-stu-id="589a9-136">Example</span></span>  
 <span data-ttu-id="589a9-137">次の例では、指定したログ ファイルに記録されたすべてのイベントの値を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="589a9-137">The following example shows how to retrieve values for all logged events in a specified log file.</span></span> <span data-ttu-id="589a9-138">この例を実行するには、を \<*Instance_Name*> のインスタンスの名前 (' Instance1 ' など) に置き換え、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ' File_Name ' をエラーログファイルの名前 (' log. 1 ' など) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="589a9-138">To run the example, replace \<*Instance_Name*> with the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as 'Instance1', and replace 'File_Name' with the name of the error log file, such as 'ERRORLOG.1'.</span></span>  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a><span data-ttu-id="589a9-139">説明</span><span class="sxs-lookup"><span data-stu-id="589a9-139">Comments</span></span>  
 <span data-ttu-id="589a9-140">WQL ステートメントで*InstanceName*または*FileName*が指定されていない場合、クエリは既定のインスタンスと現在のログファイルに関する情報を返し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="589a9-140">When *InstanceName* or *FileName* are not provided in the WQL statement, the query will return information for the default instance and the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span> <span data-ttu-id="589a9-141">たとえば、次の WQL ステートメントは、既定のインスタンス (MSSQLSERVER) 上の現在のログ ファイル (ERRORLOG) に含まれるすべてのログ イベントを返します。</span><span class="sxs-lookup"><span data-stu-id="589a9-141">For example, the following WQL statement will return all log events from the current log file (ERRORLOG) on the default instance (MSSQLSERVER).</span></span>  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a><span data-ttu-id="589a9-142">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="589a9-142">Security</span></span>  
 <span data-ttu-id="589a9-143">WMI を使用してログファイルに接続するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ローカルコンピューターとリモートコンピューターの両方に対して次のアクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="589a9-143">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file through WMI, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="589a9-144">**Root\Microsoft\SqlServer\ComputerManagement10** WMI 名前空間への読み取りアクセス。</span><span class="sxs-lookup"><span data-stu-id="589a9-144">Read access to the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace.</span></span> <span data-ttu-id="589a9-145">既定では、すべてのユーザーがアカウントの有効化権限による読み取りアクセスを持ちます。</span><span class="sxs-lookup"><span data-stu-id="589a9-145">By default, everyone has read access through the Enable Account permission.</span></span>  
  
-   <span data-ttu-id="589a9-146">エラー ログを格納したフォルダーへの読み取り権限。</span><span class="sxs-lookup"><span data-stu-id="589a9-146">Read permission to the folder that contains the error logs.</span></span> <span data-ttu-id="589a9-147">既定では、エラーログは次のパスにあり \<*Drive> ます (\* は、がインストールされているドライブを表し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<*InstanceName*> はのインスタンスの名前です [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )。</span><span class="sxs-lookup"><span data-stu-id="589a9-147">By default the error logs are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="589a9-148">\*\* \<Drive> : Server\MSSQL12\*\* **。 \<InstanceName>\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="589a9-148">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL12** **.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="589a9-149">ファイアウォール経由で接続する場合は、リモート ターゲット コンピューターのファイアウォールで WMI 用に例外が設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="589a9-149">If you are connecting through a firewall, ensure that an exception is set in the firewall for WMI on remote target computers.</span></span> <span data-ttu-id="589a9-150">詳細については、「 [Windows Vista 以降で WMI にリモート接続する](https://go.microsoft.com/fwlink/?LinkId=178848)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="589a9-150">For more information, see [Connecting to WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="589a9-151">参照</span><span class="sxs-lookup"><span data-stu-id="589a9-151">See Also</span></span>  
 <span data-ttu-id="589a9-152">[SqlErrorLogFile クラス](sqlerrorlogfile-class.md) </span><span class="sxs-lookup"><span data-stu-id="589a9-152">[SqlErrorLogFile Class](sqlerrorlogfile-class.md) </span></span>  
 [<span data-ttu-id="589a9-153">オフライン ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="589a9-153">View Offline Log Files</span></span>](../logs/view-offline-log-files.md)  
  
  
