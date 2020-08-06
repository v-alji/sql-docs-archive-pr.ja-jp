---
title: SqlErrorLogFile クラス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d73f97ebddd7a1d18c73a2cbce7fe79dafc17a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712898"
---
# <a name="sqlerrorlogfile-class"></a><span data-ttu-id="815b5-102">SqlErrorLogFile クラス</span><span class="sxs-lookup"><span data-stu-id="815b5-102">SqlErrorLogFile Class</span></span>
  <span data-ttu-id="815b5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルの情報の表示に関するプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="815b5-103">Provides properties for viewing information about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815b5-104">構文</span><span class="sxs-lookup"><span data-stu-id="815b5-104">Syntax</span></span>  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a><span data-ttu-id="815b5-105">Properties</span><span class="sxs-lookup"><span data-stu-id="815b5-105">Properties</span></span>  
 <span data-ttu-id="815b5-106">SQLErrorLogFile クラスは、次のプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="815b5-106">The SQLErrorLogFile class defines the following properties.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="815b5-107">ArchiveNumber</span><span class="sxs-lookup"><span data-stu-id="815b5-107">ArchiveNumber</span></span>|<span data-ttu-id="815b5-108">データ型: `uint32`</span><span class="sxs-lookup"><span data-stu-id="815b5-108">Data type: `uint32`</span></span><br /><br /> <span data-ttu-id="815b5-109">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="815b5-109">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="815b5-110">ログ ファイルのアーカイブ番号。</span><span class="sxs-lookup"><span data-stu-id="815b5-110">The archive number for the log file.</span></span>|  
|<span data-ttu-id="815b5-111">InstanceName</span><span class="sxs-lookup"><span data-stu-id="815b5-111">InstanceName</span></span>|<span data-ttu-id="815b5-112">データ型: `string`</span><span class="sxs-lookup"><span data-stu-id="815b5-112">Data type: `string`</span></span><br /><br /> <span data-ttu-id="815b5-113">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="815b5-113">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="815b5-114">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="815b5-114">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="815b5-115">ログ ファイルが存在する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="815b5-115">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the log file resides.</span></span>|  
|<span data-ttu-id="815b5-116">LastModified</span><span class="sxs-lookup"><span data-stu-id="815b5-116">LastModified</span></span>|<span data-ttu-id="815b5-117">データ型: `datetime`</span><span class="sxs-lookup"><span data-stu-id="815b5-117">Data type: `datetime`</span></span><br /><br /> <span data-ttu-id="815b5-118">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="815b5-118">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="815b5-119">ログ ファイルの最終変更日。</span><span class="sxs-lookup"><span data-stu-id="815b5-119">The date that the log file was last modified.</span></span>|  
|<span data-ttu-id="815b5-120">LogFileSize</span><span class="sxs-lookup"><span data-stu-id="815b5-120">LogFileSize</span></span>|<span data-ttu-id="815b5-121">データ型: `uint32`</span><span class="sxs-lookup"><span data-stu-id="815b5-121">Data type: `uint32`</span></span><br /><br /> <span data-ttu-id="815b5-122">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="815b5-122">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="815b5-123">ログ ファイルのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="815b5-123">The log file size, in bytes.</span></span>|  
|<span data-ttu-id="815b5-124">名前</span><span class="sxs-lookup"><span data-stu-id="815b5-124">Name</span></span>|<span data-ttu-id="815b5-125">データ型: `string`</span><span class="sxs-lookup"><span data-stu-id="815b5-125">Data type: `string`</span></span><br /><br /> <span data-ttu-id="815b5-126">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="815b5-126">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="815b5-127">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="815b5-127">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="815b5-128">ログ ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="815b5-128">The name of the log file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="815b5-129">解説</span><span class="sxs-lookup"><span data-stu-id="815b5-129">Remarks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="815b5-130">MOF</span><span class="sxs-lookup"><span data-stu-id="815b5-130">MOF</span></span>|<span data-ttu-id="815b5-131">Sqlmgmprovider xpsp2up.mof</span><span class="sxs-lookup"><span data-stu-id="815b5-131">Sqlmgmprovider xpsp2up.mof</span></span>|  
|<span data-ttu-id="815b5-132">[DLL]</span><span class="sxs-lookup"><span data-stu-id="815b5-132">DLL</span></span>|<span data-ttu-id="815b5-133">Sqlmgmprovider.dll</span><span class="sxs-lookup"><span data-stu-id="815b5-133">Sqlmgmprovider.dll</span></span>|  
|<span data-ttu-id="815b5-134">名前空間</span><span class="sxs-lookup"><span data-stu-id="815b5-134">Namespace</span></span>|<span data-ttu-id="815b5-135">\root\Microsoft\SqlServer\ComputerManagement10</span><span class="sxs-lookup"><span data-stu-id="815b5-135">\root\Microsoft\SqlServer\ComputerManagement10</span></span>|  
  
## <a name="example"></a><span data-ttu-id="815b5-136">例</span><span class="sxs-lookup"><span data-stu-id="815b5-136">Example</span></span>  
 <span data-ttu-id="815b5-137">次の例では、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にあるすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="815b5-137">The following example retrieves information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files on a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="815b5-138">この例を実行するには、を \<*Instance_Name*> インスタンスの名前 (' Instance1 ' など) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="815b5-138">To run the example, replace \<*Instance_Name*> with the name of the instance, for example, 'Instance1'.</span></span>  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a><span data-ttu-id="815b5-139">説明</span><span class="sxs-lookup"><span data-stu-id="815b5-139">Comments</span></span>  
 <span data-ttu-id="815b5-140">WQL ステートメントで*InstanceName*が指定されていない場合、クエリは既定のインスタンスの情報を返します。</span><span class="sxs-lookup"><span data-stu-id="815b5-140">When *InstanceName* is not provided in the WQL statement, the query will return information for the default instance.</span></span> <span data-ttu-id="815b5-141">たとえば、次の WQL ステートメントは、既定のインスタンス (MSSQLSERVER) からすべてのログ ファイルに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="815b5-141">For example, the following WQL statement will return information about all log files from the default instance (MSSQLSERVER).</span></span>  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a><span data-ttu-id="815b5-142">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="815b5-142">Security</span></span>  
 <span data-ttu-id="815b5-143">WMI を使用してログファイルに接続するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ローカルコンピューターとリモートコンピューターの両方に対して次のアクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="815b5-143">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file through WMI, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="815b5-144">**Root\Microsoft\SqlServer\ComputerManagement10** WMI 名前空間への読み取りアクセス。</span><span class="sxs-lookup"><span data-stu-id="815b5-144">Read access to the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace.</span></span> <span data-ttu-id="815b5-145">既定では、すべてのユーザーがアカウントの有効化権限による読み取りアクセスを持ちます。</span><span class="sxs-lookup"><span data-stu-id="815b5-145">By default, everyone has read access through the Enable Account permission.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="815b5-146">WMI のアクセス許可を確認する方法については、「[オフラインログファイルの表示](../logs/view-offline-log-files.md)」の「セキュリティ」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="815b5-146">For information about how to verify WMI permissions, see the Security section of the topic [View Offline Log Files](../logs/view-offline-log-files.md).</span></span>  
  
-   <span data-ttu-id="815b5-147">エラー ログを格納したフォルダーへの読み取り権限。</span><span class="sxs-lookup"><span data-stu-id="815b5-147">Read permission to the folder that contains the error logs.</span></span> <span data-ttu-id="815b5-148">既定では、エラーログは次のパスにあり \<*Drive> ます (\* は、がインストールされているドライブを表し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<*InstanceName*> はのインスタンスの名前です [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )。</span><span class="sxs-lookup"><span data-stu-id="815b5-148">By default the error logs are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="815b5-149">\*\* \<Drive> : Server\MSSQL11\*\* **。 \<InstanceName>\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="815b5-149">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL11** **.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="815b5-150">ファイアウォール経由で接続する場合は、リモート ターゲット コンピューターのファイアウォールで WMI 用に例外が設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="815b5-150">If you are connecting through a firewall, ensure that an exception is set in the firewall for WMI on remote target computers.</span></span> <span data-ttu-id="815b5-151">詳細については、「 [Windows Vista 以降で WMI にリモート接続する](https://go.microsoft.com/fwlink/?LinkId=178848)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="815b5-151">For more information, see [Connecting to WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815b5-152">参照</span><span class="sxs-lookup"><span data-stu-id="815b5-152">See Also</span></span>  
 <span data-ttu-id="815b5-153">[SqlErrorLogEvent クラス](sqlerrorlogevent-class.md) </span><span class="sxs-lookup"><span data-stu-id="815b5-153">[SqlErrorLogEvent Class](sqlerrorlogevent-class.md) </span></span>  
 [<span data-ttu-id="815b5-154">オフライン ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="815b5-154">View Offline Log Files</span></span>](../logs/view-offline-log-files.md)  
  
  
