

# Storage Blobs Quickstart (async)

The following sample is a rewrite of the [Azure Storage Blobs Quickstart](https://github.com/Azure-Samples/storage-blobs-node-quickstart) by updating the sample in the following ways:

- **Uses async/await**: The [Azure Storage SDK API](https://github.com/Azure/azure-storage-node) is still callback-based, but the approach in this sample modernizes the syntax. API calls are wrapped in `Promises` and executed in the context of an `async/await` operation.

- **Command-based interaction**: Rather than all operations executing sequentially, you are able to explicitly tell the script which operation to execute (ex: upload, list, etc.)
 
- **Uses environment variables**: Instead of hard-coding the blob storage connection string in the `.js` file, this sample accesses the connection string from an environment variable. The use of environment variables is more representative of how you would access sensitive information in production.

- **Based on a single file**: The original sample uses a technique to create unique file names which allows you to easily upload multiple files. The approach in this sample attempts to simplify the process and only allows you to manipulate one file named `example.txt`.

To run this sample you need an [Azure account](https://azure.microsoft.com/free/), a [blob storage account](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account) and the associated blob storage connection string.

## Set up
First, clone the repository on your machine:

    git clone https://github.com/craigshoemaker/blob-storage-quickstart-async.git

Then, switch to the appropriate folder:

    cd blob-storage-quickstart-async

Next, install the dependencies:

    npm install

Now, add your blob storage connection string as an environment variable named `AZURE_STORAGE_CONNECTION_STRING` to a file named `.env`.

> **Note**: The repository includes a file named `.env.example`. You can rename this file by removing `.example` and adding the correct value for your connection string in the `.env` file.

## Running the sample

Once the setup steps are complete, you can interact with the sample by passing a command into the `--command` parameter.

For instance if you want to create a container in blob storage, then run the following command:

    node index.js --command createContainer

Commands available include:


| Command | Description |
|---------|---------|
|`createContainer` | Creates a container named `test` (succeeds even if container already exists) |
|`upload`          | Uploads the `example.txt` file |
|`download`        | Downloads the contents of the `example` blob to `example.txt` |
|`delete`          | Deletes the `example` blob |
|`list`            | Lists the contents of the `test` container to the console |

## Resources

You can use the [Azure Storage explorer](https://azure.microsoft.com/features/storage-explorer/) to see the data in your Azure account.