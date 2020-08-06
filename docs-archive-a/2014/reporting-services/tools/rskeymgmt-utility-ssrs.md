---
title: rskeymgmt ユーティリティ (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], encryption
- joining report server instances [SQL Server]
- report server scale-out deployments [Reporting Services]
- cryptography [Reporting Services]
- multiple report server instances
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], scale-out deployments
- encryption [Reporting Services]
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 53f1318d-bd2d-4c08-b19f-c8b698b5b3d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae4bdd6656cf5b29f8fd40fcf730f49a6de8f32e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721020"
---
# <a name="rskeymgmt-utility-ssrs"></a><span data-ttu-id="dde22-102">rskeymgmt ユーティリティ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="dde22-102">rskeymgmt Utility (SSRS)</span></span>
  <span data-ttu-id="dde22-103">重要なレポート サーバー データを不正アクセスから保護するための対称キーを、抽出、復元、作成、および削除します。</span><span class="sxs-lookup"><span data-stu-id="dde22-103">Extracts, restores, creates, and deletes the symmetric key used to protect sensitive report server data against unauthorized access.</span></span> <span data-ttu-id="dde22-104">また、このユーティリティは、レポート サーバー インスタンスをスケール アウト配置に追加する場合にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-104">This utility is also used to join report server instances in a scale-out deployment.</span></span> <span data-ttu-id="dde22-105">*レポート サーバーのスケール アウト配置* とは、複数のレポート サーバー インスタンスが 1 つのレポート サーバー データベースを共有する状態を表しています。</span><span class="sxs-lookup"><span data-stu-id="dde22-105">A *report server scale-out deployment* refers to multiple report server instances that share a single report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde22-106">構文</span><span class="sxs-lookup"><span data-stu-id="dde22-106">Syntax</span></span>  
  
```  
  
      rskeymgmt {-?}  
{-eextract}  
{-aapply}  
{-ddeleteall}  
{-srecreatekey}  
{-rremoveinstancekey}  
{-jjoinfarm}  
{-iinstance}  
{-ffile}  
{-pencryptionpassword}  
{-mremotecomputer}  
{-ninstancenameofremotecomputer}  
{-uadministratoruseraccount}  
{-vadministratorpassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="dde22-107">引数</span><span class="sxs-lookup"><span data-stu-id="dde22-107">Arguments</span></span>  
 <span data-ttu-id="dde22-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="dde22-108">**-?**</span></span>  
 <span data-ttu-id="dde22-109">**rskeymgmt** の引数の構文を表示します。</span><span class="sxs-lookup"><span data-stu-id="dde22-109">Displays the syntax of **rskeymgmt** arguments.</span></span>  
  
 <span data-ttu-id="dde22-110">**-e**</span><span class="sxs-lookup"><span data-stu-id="dde22-110">**-e**</span></span>  
 <span data-ttu-id="dde22-111">レポート サーバー インスタンスのデータを暗号化したり、暗号化の解除を行うための対称キーを抽出します。このキーにより、ファイルへのデータのコピーが可能になります。</span><span class="sxs-lookup"><span data-stu-id="dde22-111">Extracts the symmetric key used to encrypt and decrypt data for the report server instance so that you can copy it to a file.</span></span>  
  
 <span data-ttu-id="dde22-112">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="dde22-112">This argument does not take a value.</span></span> <span data-ttu-id="dde22-113">ただし、抽出を完了するには、コマンド ラインに他の引数を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-113">However, you must include additional arguments on the command line to complete the extraction.</span></span> <span data-ttu-id="dde22-114">指定する必要のある引数は、`-f` および `-p` です。</span><span class="sxs-lookup"><span data-stu-id="dde22-114">The arguments that you must specify include `-f` and`-p`.</span></span>  
  
 <span data-ttu-id="dde22-115">**-a**</span><span class="sxs-lookup"><span data-stu-id="dde22-115">**-a**</span></span>  
 <span data-ttu-id="dde22-116">既存の対称キーを、パスワードで保護されたバックアップ ファイル内に作成したコピーと置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dde22-116">Replaces an existing symmetric key with a copy that you provide in a password protected backup file.</span></span> <span data-ttu-id="dde22-117">対称キーのすべてのインスタンスが更新されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-117">All instances of the symmetric key are updated.</span></span>  
  
 <span data-ttu-id="dde22-118">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="dde22-118">This argument does not take a value.</span></span> <span data-ttu-id="dde22-119">ただし、適用するキーを含むファイルを選択するには、コマンド ラインに他の引数を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-119">However, you must include additional arguments on the command line to select the file that contains the key to be applied.</span></span> <span data-ttu-id="dde22-120">指定できる引数は、`-f` および `-p` です。</span><span class="sxs-lookup"><span data-stu-id="dde22-120">The arguments that you can specify include `-f` and`-p`.</span></span>  
  
 <span data-ttu-id="dde22-121">**-d**</span><span class="sxs-lookup"><span data-stu-id="dde22-121">**-d**</span></span>  
 <span data-ttu-id="dde22-122">レポート サーバー データベース内にある、すべての対称キー インスタンスと暗号化されたデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="dde22-122">Deletes all symmetric key instances and all encrypted data in a report server database.</span></span> <span data-ttu-id="dde22-123">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="dde22-123">This argument does not take a value.</span></span>  
  
 `-s`  
 <span data-ttu-id="dde22-124">新規の対称キーを生成し、この新規のキーを使用してすべての暗号化された内容を再暗号化します。</span><span class="sxs-lookup"><span data-stu-id="dde22-124">Generates a new symmetric key and re-encrypts all encrypted content using the new key.</span></span> <span data-ttu-id="dde22-125">対称キーのすべてのインスタンスが再生成されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-125">All instances of the symmetric key are regenerated.</span></span>  
  
 `-j`  
 <span data-ttu-id="dde22-126">リモート レポート サーバー インスタンスが、ローカル レポート サーバー インスタンスによって使用されるレポート サーバー データベースを共有するように構成します。</span><span class="sxs-lookup"><span data-stu-id="dde22-126">Configures a remote report server instance to share the report server database that is used by the local report server instance.</span></span>  
  
 <span data-ttu-id="dde22-127">**-r**  *installationID*</span><span class="sxs-lookup"><span data-stu-id="dde22-127">**-r**  *installationID*</span></span>  
 <span data-ttu-id="dde22-128">特定のレポート サーバー インスタンスに対する対称キー情報を削除します。これにより、レポート サーバーはスケールアウト配置から削除されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-128">Removes the symmetric key information for a specific report server instance, thereby removing the report server from a scale-out deployment.</span></span> <span data-ttu-id="dde22-129">*installationID* は、RSReportserver.config ファイルにある GUID 値です。</span><span class="sxs-lookup"><span data-stu-id="dde22-129">The *installationID* is a GUID value that can be found in the RSReportserver.config file.</span></span>  
  
 <span data-ttu-id="dde22-130">`-f`  *拡張子*</span><span class="sxs-lookup"><span data-stu-id="dde22-130">`-f`  *file*</span></span>  
 <span data-ttu-id="dde22-131">対称キーのバックアップ コピーが格納されるファイルへの完全修飾パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-131">Specifies a fully qualified path to the file that stores a backup copy of the symmetric keys.</span></span>  
  
 <span data-ttu-id="dde22-132">**rskeymgmt -e**を使用すると、対称キーは指定したファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="dde22-132">For **rskeymgmt -e**, the symmetric key is written to the file you specify.</span></span>  
  
 <span data-ttu-id="dde22-133">**rskeymgmt -a**を使用すると、ファイルに格納された対称キーの値がレポート サーバー インスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-133">For **rskeymgmt -a**, the symmetric key value stored in the file is applied to the report server instance.</span></span>  
  
 <span data-ttu-id="dde22-134">`-p`  *password*</span><span class="sxs-lookup"><span data-stu-id="dde22-134">`-p`  *password*</span></span>  
 <span data-ttu-id="dde22-135">(`-f` を使用する場合は必須) 対称キーのバックアップや適用に使用されるパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-135">(Required for `-f`) Specifies the password used to back up or apply a symmetric key.</span></span> <span data-ttu-id="dde22-136">この値は空にできません。</span><span class="sxs-lookup"><span data-stu-id="dde22-136">This value cannot be empty.</span></span>  
  
 `-i`  
 <span data-ttu-id="dde22-137">ローカル レポート サーバー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-137">Specifies a local report server instance.</span></span> <span data-ttu-id="dde22-138">レポート サーバーを既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにインストールした場合、この引数は省略できます (`-i` の既定値は MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="dde22-138">This argument is optional if you installed the report server on the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (the default value for `-i` is MSSQLSERVER).</span></span> <span data-ttu-id="dde22-139">レポート サーバーを名前付きインスタンスとしてインストールした場合は、`-i` は必須です。</span><span class="sxs-lookup"><span data-stu-id="dde22-139">If you installed the report server as a named instance, `-i` is required.</span></span>  
  
 `-m`  
 <span data-ttu-id="dde22-140">レポート サーバー インスタンスをレポート サーバーのスケール アウト配置に追加する場合、このレポート サーバー インスタンスをホストするリモート コンピューターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-140">Specifies the name of the remote computer that hosts the report server instance you are joining to the report server scale-out deployment.</span></span> <span data-ttu-id="dde22-141">ネットワーク上で識別されるコンピューターの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="dde22-141">Use the name of the computer that identifies it on your network.</span></span>  
  
 `-n`  
 <span data-ttu-id="dde22-142">リモート コンピューター上のレポート サーバー インスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-142">Specifies the name of the report server instance on a remote computer.</span></span> <span data-ttu-id="dde22-143">レポート サーバーを既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにインストールした場合、この引数は省略できます (`-n` の既定値は MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="dde22-143">This argument is optional if you installed the report server on the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (the default value for `-n` is MSSQLSERVER).</span></span> <span data-ttu-id="dde22-144">レポート サーバーを名前付きインスタンスとしてインストールした場合は、`-n` は必須です。</span><span class="sxs-lookup"><span data-stu-id="dde22-144">If you installed the report server as a named instance, `-n` is required.</span></span>  
  
 <span data-ttu-id="dde22-145">`-u`  *useraccount*</span><span class="sxs-lookup"><span data-stu-id="dde22-145">`-u`  *useraccount*</span></span>  
 <span data-ttu-id="dde22-146">スケールアウト配置に追加するリモート コンピューター上の管理者アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-146">Specifies the administrator account on the remote computer that you are joining to the scale-out deployment.</span></span> <span data-ttu-id="dde22-147">アカウントが指定されない場合は、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-147">If an account is not specified, the credentials of the current user are used.</span></span>  
  
 <span data-ttu-id="dde22-148">`-v`  *password*</span><span class="sxs-lookup"><span data-stu-id="dde22-148">`-v`  *password*</span></span>  
 <span data-ttu-id="dde22-149">(`-u` を使用する場合は必須) スケールアウト配置に追加するリモート コンピューター上の管理者アカウントのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-149">(Required for `-u`) Specifies the password of an administrator account on the remote computer that you want to join to the scale-out deployment.</span></span>  
  
 <span data-ttu-id="dde22-150">**-t**  *トレース*</span><span class="sxs-lookup"><span data-stu-id="dde22-150">**-t**  *trace*</span></span>  
 <span data-ttu-id="dde22-151">エラー メッセージをトレース ログに出力します。</span><span class="sxs-lookup"><span data-stu-id="dde22-151">Outputs error messages to the trace log.</span></span> <span data-ttu-id="dde22-152">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="dde22-152">This argument does not take a value.</span></span> <span data-ttu-id="dde22-153">詳細については、「 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dde22-153">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="dde22-154">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="dde22-154">Permissions</span></span>  
 <span data-ttu-id="dde22-155">このツールを実行するには、ローカル管理者であることが必要です。また、このツールは、レポート サーバーをホストするコンピューター上でローカルに実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-155">You must be a local administrator to run the tool, and you must run it locally on the computer that hosts the report server.</span></span> <span data-ttu-id="dde22-156">rskeymgmt ユーティリティは、ローカルのレポート サーバー Windows インスタンスと連動します (このユーティリティはレポート サーバー Windows サービスのリモート インスタンスに接続できないので、このユーティリティを使用してリモート レポート サーバー インスタンスの暗号化キーを管理することはできません)。</span><span class="sxs-lookup"><span data-stu-id="dde22-156">The rskeymgmt utility works with the local Report Server Windows instance (the utility cannot connect to remote instances of the Report Server Windows service so it cannot be used to manage the encryption keys of a remote report server instance).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dde22-157">`-u` 引数と `-v` 引数を使用する場合、リモート コンピューターに対する管理者権限を持つアカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-157">If you are using the `-u` and `-v` arguments, be sure to specify an account that has administrator permissions on the remote computer.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dde22-158">例</span><span class="sxs-lookup"><span data-stu-id="dde22-158">Examples</span></span>  
 <span data-ttu-id="dde22-159">次の例は、 **rskeymgmt**の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dde22-159">The following examples illustrate ways of using **rskeymgmt**.</span></span> <span data-ttu-id="dde22-160">これらの例では、暗号化キーの抽出、復元、削除の実行、およびレポート サーバーのスケールアウト配置の構成を行います。</span><span class="sxs-lookup"><span data-stu-id="dde22-160">The following examples show how to extract, restore, and delete encryption keys, and how to configure a report server scale-out deployment.</span></span>  
  
#### <a name="extracting-encryption-keys"></a><span data-ttu-id="dde22-161">暗号化キーの抽出</span><span class="sxs-lookup"><span data-stu-id="dde22-161">Extracting Encryption Keys</span></span>  
 <span data-ttu-id="dde22-162">次の例では、暗号化キーのバックアップ コピーを作成し、そのコピーをパスワードで保護されたファイルとしてフロッピー ディスク上に保存します。</span><span class="sxs-lookup"><span data-stu-id="dde22-162">This example shows how to create a backup copy of the encryption key and save it to a password-protected file on a floppy disk.</span></span> <span data-ttu-id="dde22-163">レポート サーバーが名前付きインスタンスとしてインストールされている場合は、`-i` 引数を追加します。</span><span class="sxs-lookup"><span data-stu-id="dde22-163">If the report server is installed as a named instance, add the `-i` argument.</span></span>  
  
```  
rskeymgmt -e -f a:\backupkey\keys -p <password>  
```  
  
#### <a name="restoring-encryption-keys"></a><span data-ttu-id="dde22-164">暗号化キーの復元</span><span class="sxs-lookup"><span data-stu-id="dde22-164">Restoring Encryption Keys</span></span>  
 <span data-ttu-id="dde22-165">次の例では、暗号化キーを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dde22-165">This example shows how to replace the encryption key.</span></span> <span data-ttu-id="dde22-166">キーのバックアップ コピーの場所およびファイルのロックを解除するパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-166">You must specify the location of the backup copy of the key and the password that unlocks the file.</span></span>  
  
```  
rskeymgmt -a -f a:\backupkey\keys -p <password>  
```  
  
#### <a name="deleting-encryption-keys-and-encrypted-content"></a><span data-ttu-id="dde22-167">暗号化キーおよび暗号化された内容の削除</span><span class="sxs-lookup"><span data-stu-id="dde22-167">Deleting Encryption Keys and Encrypted Content</span></span>  
 <span data-ttu-id="dde22-168">次の例では、レポート サーバーに格納されたすべての暗号化キーを削除します。</span><span class="sxs-lookup"><span data-stu-id="dde22-168">This example shows how to delete all encryption keys stored in a report server.</span></span> <span data-ttu-id="dde22-169">インストール環境がレポート サーバーのスケール アウト配置になっている場合は、この配置に含まれているすべてのレポート サーバー インスタンスに対する暗号化キーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-169">If your installation is a report server scale-out deployment, the encryption keys for all report server instances that are included in the deployment will be deleted.</span></span> <span data-ttu-id="dde22-170">また、暗号化キーを削除すると、レポート サーバー データベースにある既存の暗号化された値はすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-170">Deleting an encryption key also deletes any existing encrypted values in the report server database.</span></span> <span data-ttu-id="dde22-171">暗号化されたコンテンツの詳細については、「[暗号化されたレポート サーバー データの格納 (SSRS 構成マネージャー)](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dde22-171">For more information about encrypted content, see [Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md).</span></span>  
  
```  
rskeymgmt -d  
```  
  
#### <a name="joining-a-remote-report-server-named-instance-to-a-scale-out-deployment"></a><span data-ttu-id="dde22-172">スケール アウト配置へのリモート レポート サーバー名前付きインスタンスの追加</span><span class="sxs-lookup"><span data-stu-id="dde22-172">Joining a Remote Report Server Named Instance to a Scale-out Deployment</span></span>  
 <span data-ttu-id="dde22-173">次の例では、リモート コンピューターにインストールされたレポート サーバー インスタンスを、レポート サーバーのスケール アウト配置に追加します。</span><span class="sxs-lookup"><span data-stu-id="dde22-173">This example shows how to add a report server instance that is installed on a remote computer to a report server scale-out deployment.</span></span> <span data-ttu-id="dde22-174">このコマンドは、共有データベースの使用が既に構成されているコンピューターのいずれかで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-174">You must run the command on one of the computers that is already configured to use the shared database.</span></span> <span data-ttu-id="dde22-175">このコマンドの引数には、スケール アウト配置に追加するリモート レポート サーバー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-175">The command arguments specify the remote report server instance you want to join to the scale-out deployment.</span></span>  
  
```  
rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="dde22-176">レポート サーバーのスケール アウト配置とは、複数のレポート サーバー インスタンスが同じレポート サーバー データベースを共有する配置モデルのことです。</span><span class="sxs-lookup"><span data-stu-id="dde22-176">A report server scale-out deployment refers to a deployment model where multiple report server instances share the same report server database.</span></span> <span data-ttu-id="dde22-177">対称キーをデータベースに格納するレポート サーバー インスタンスであれば、レポート サーバー データベースを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="dde22-177">A report server database can be used by any report server instance that stores its symmetric keys in the database.</span></span> <span data-ttu-id="dde22-178">たとえば、レポート サーバー データベースが 3 つのレポート サーバー インスタンスに対するキー情報を含んでいる場合、3 つすべてのインスタンスは、同じスケール アウト配置のメンバーと見なされます。</span><span class="sxs-lookup"><span data-stu-id="dde22-178">For example, if a report server database contains key information for three report server instances, all three instances are considered to members of the same scale-out deployment.</span></span>  
  
#### <a name="joining-report-server-instances-on-the-same-computer"></a><span data-ttu-id="dde22-179">同じコンピューター上の複数のレポート サーバー インスタンスの追加</span><span class="sxs-lookup"><span data-stu-id="dde22-179">Joining Report Server Instances on the Same Computer</span></span>  
 <span data-ttu-id="dde22-180">同じコンピューターにインストールされている複数のレポート サーバー インスタンスから、スケール アウト配置を作成できます。</span><span class="sxs-lookup"><span data-stu-id="dde22-180">You can create a scale-out deployment from multiple report server instances that are installed on the same computer.</span></span> <span data-ttu-id="dde22-181">ローカルにインストールされているレポート サーバー インスタンスを追加する場合、`-u` および `-v` 引数は設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="dde22-181">Do not set the `-u` and `-v` arguments if you are joining report server instances that are installed locally.</span></span> <span data-ttu-id="dde22-182">`-u` および `-v` 引数は、リモート コンピューターからインスタンスを追加する場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="dde22-182">The `-u` and `-v` arguments are used only when you are joining an instance from a remote computer.</span></span> <span data-ttu-id="dde22-183">これらの引数を指定すると、"ユーザー資格情報はローカル接続には使用できません" というエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-183">If you specify the arguments, you will get the following error: "User credentials cannot be used for local connections."</span></span>  
  
 <span data-ttu-id="dde22-184">次の例は、複数のローカル インスタンスを使用してスケール アウト配置を作成する構文です。</span><span class="sxs-lookup"><span data-stu-id="dde22-184">The following example illustrates the syntax for creating a scale-out deployment using multiple local instances.</span></span> <span data-ttu-id="dde22-185">この例では、<`initializedinstance`> は、レポートサーバーデータベースを使用するように既に初期化されているインスタンスの名前です `newinstance` 。 <> は、配置に追加するインスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="dde22-185">In this example, <`initializedinstance`> is the name of an instance that is already initialized to use the report server database, and <`newinstance`> is the name of the instance that you want to add to the deployment:</span></span>  
  
```  
rskeymgmt -j -i <initializedinstance> -m <computer name> -n <newinstance>  
```  
  
#### <a name="removing-encryption-keys-for-a-single-report-server-in-a-scale-out-deployment"></a><span data-ttu-id="dde22-186">スケール アウト配置に含まれる 1 つのレポート サーバーに対する暗号化キーの削除</span><span class="sxs-lookup"><span data-stu-id="dde22-186">Removing Encryption Keys for a Single Report Server in a Scale-out Deployment</span></span>  
 <span data-ttu-id="dde22-187">次の例では、レポート サーバーのスケール アウト配置に含まれている 1 つのレポート サーバーに対する暗号化キーを削除します。</span><span class="sxs-lookup"><span data-stu-id="dde22-187">This example shows how to remove the encryption keys for a single report server in a report server scale-out deployment.</span></span> <span data-ttu-id="dde22-188">これらのキーは、レポート サーバー データベースから削除されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-188">The keys are removed from the report server database.</span></span> <span data-ttu-id="dde22-189">レポート サーバー インスタンスに対するキーが削除されると、そのレポート サーバー インスタンスはデータベース内の暗号化されたデータにはアクセスできなくなるため、スケール アウト配置からの削除が効率的に行われます。</span><span class="sxs-lookup"><span data-stu-id="dde22-189">Once the keys for that report server instance are removed, that report server instance can no longer access encrypted data in the database, effectively removing it from the scale-out deployment.</span></span>  
  
 <span data-ttu-id="dde22-190">レポート サーバー インスタンスをスケールアウト配置から削除するには、インストール ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-190">Removing a report server instance from a scale-out deployment requires you to specify an installation ID.</span></span> <span data-ttu-id="dde22-191">インストール ID とは、暗号化キーを削除するレポート サーバー インスタンスの RSReportserver.config ファイルに格納されている GUID のことです。</span><span class="sxs-lookup"><span data-stu-id="dde22-191">The installation ID is a GUID stored in the RSReportserver.config file of the report server instance for which you want to remove encryption keys.</span></span> <span data-ttu-id="dde22-192">スケール アウト配置から削除するコンピューター上で次のコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-192">You must run the following command on the computer that you want to remove from the scale-out deployment.</span></span> <span data-ttu-id="dde22-193">レポート サーバーが名前付きインスタンスとしてインストールされている場合は、`-i` 引数を使用してインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dde22-193">If the report server is installed as a named instance, use the `-i` argument to specify the instance.</span></span> <span data-ttu-id="dde22-194">詳しくは、「 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dde22-194">For more information, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
```  
rskeymgmt -r <installationID>  
```  
  
## <a name="file-location"></a><span data-ttu-id="dde22-195">ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="dde22-195">File Location</span></span>  
 <span data-ttu-id="dde22-196">Rskeymgmt.exe は、 \*\* \<*drive*> Server\110\Tools\Binn**にあります。または、 \*\* \<*drive*> \Microsoft sql Server\110\Tools\Binn**にあります。</span><span class="sxs-lookup"><span data-stu-id="dde22-196">Rskeymgmt.exe is located at **\<*drive*>:\Program Files\Microsoft SQL Server\110\Tools\Binn** or at **\<*drive*>:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="dde22-197">このユーティリティは、ファイル システム上の任意のフォルダーから実行できます。</span><span class="sxs-lookup"><span data-stu-id="dde22-197">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dde22-198">解説</span><span class="sxs-lookup"><span data-stu-id="dde22-198">Remarks</span></span>  
 <span data-ttu-id="dde22-199">レポート サーバーは、格納された資格情報および接続情報を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="dde22-199">A report server encrypts stored credentials and connection information.</span></span> <span data-ttu-id="dde22-200">データの暗号化には、公開キーおよび対称キーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-200">A public key and a symmetric key are used to encrypt data.</span></span> <span data-ttu-id="dde22-201">レポート サーバーを実行するには、レポート サーバー データベースに有効なキーが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-201">A report server database must have valid keys in order for the report server to run.</span></span> <span data-ttu-id="dde22-202">キーのバックアップ、削除、復元を行うには **rskeymgmt** を使用します。</span><span class="sxs-lookup"><span data-stu-id="dde22-202">You can use **rskeymgmt** to back up, delete, or restore the keys.</span></span> <span data-ttu-id="dde22-203">このツールには、キーを復元できない場合に、使用できなくなった暗号化されたコンテンツを削除する方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="dde22-203">If the keys cannot be restored, this tool provides a way to delete encrypted content that can no longer be used.</span></span>  
  
 <span data-ttu-id="dde22-204">セットアップや初期化の際に定義されるキーのセットを管理するには、 **rskeymgmt** ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="dde22-204">The **rskeymgmt** utility is used to manage the key set that is defined during Setup or during initialization.</span></span> <span data-ttu-id="dde22-205">このユーティリティは、リモート プロシージャ呼び出し (RPC) エンドポイントを介して、ローカルのレポート サーバー Windows サービスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="dde22-205">It connects to the local Report Server Windows service through a Remote Procedure Call (RPC) endpoint.</span></span> <span data-ttu-id="dde22-206">このユーティリティが動作するには、レポート サーバー Windows サービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dde22-206">The Report Server Windows service must be running in order for this utility to work.</span></span>  
  
 <span data-ttu-id="dde22-207">暗号化キーの詳細については、「[暗号化キーの構成と管理 (SSRS 構成マネージャー)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)」および「[レポート サーバーの初期化 (SSRS 構成マネージャー)](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dde22-207">For more information about the encryption keys, see [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) and [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde22-208">参照</span><span class="sxs-lookup"><span data-stu-id="dde22-208">See Also</span></span>  
 <span data-ttu-id="dde22-209">[SSRS Configuration Manager &#40;ネイティブモードのレポートサーバーのスケールアウト配置の構成&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="dde22-209">[Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) </span></span>  
 <span data-ttu-id="dde22-210">[Reporting Services レポート サーバー (ネイティブ モード)](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="dde22-210">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="dde22-211">[SSRS&#41;&#40;レポートサーバーのコマンドプロンプトユーティリティ](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dde22-211">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="dde22-212">暗号化キーの構成と管理 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="dde22-212">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
