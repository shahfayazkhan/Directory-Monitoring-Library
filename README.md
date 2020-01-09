# Directory-Monitoring-Library
Watching a Directory for Changes

To implement this functionality, called file change notification, a program must be able to detect what is happening to the relevant directory on the file system. One way to do so is to poll the file system looking for changes, but this approach is inefficient. It does not scale to applications that have hundreds of open files or directories to monitor.

Creating a Watch Service and Registering for Directory
# 1) First Create the Path String for entering a Path which you monitoring
    String path = "root_path";
    DataFiles dataFiles = new DataFiles(path);
  
# 2) Watch Directory only For Inside one Folder data Changed
    dataFiles.setOnDataSetChangeListener(new addOnDataSetChangeListener() {
        @Override
        public void onDataChanged(File file, String name) {
            System.out.println("Change : "+name);
        }

        @Override
        public void onDataFailed(Exception e) {
            System.out.println("The Error Failed : "+e);
        }
    });
    
 # 3) Watch Directory to Detect new File Added for one Folder
    dataFiles.setOnDataAddChangeListener(new addOnDataAddChangeListener() {
        @Override
        public void onDataAdded(File file, String name) {
            System.out.println("Added : "+name);
        }

        @Override
        public void onDataAddedFailed(Exception e) {
            System.out.println("Added Failed : "+e.getMessage());
        }
    });
    
# 4) Watch Directory to Detect File Remove for one Folder
    dataFiles.setOnDataRemoveChangeListener(new addOnDataRemoveChangeListener() {
        @Override
        public void onDataRemoved(File file, String name) {
            System.out.println("Removed : "+name);
        }

        @Override
        public void onDataRemovedFailed(Exception e) {
            System.out.println(e);
        }
    });

# 5) Watch Directory only For Inside SubFolders data Changed
    dataFiles.setOnAddedSubFolderChangeListener(new addOnDataAddedSubFolderChangeListener() {
        @Override
        public void onDataAdded(File file, String name) {
            System.out.println("Added : "+file.getAbsolutePath());
        }

        @Override
        public void onDataAddedFailed(Exception e) {
        System.out.println(e);
        }
    });

# 6) Watch Directory to Detect new File Added for in SubFolders
    dataFiles.setOnDataSetSubFolderChangeListener(new addOnDataSetSubFolderChangeListener() {
        @Override
        public void onDataChanged(File file, String name) {
            System.out.println("Name : "+file.getAbsolutePath());
        }

        @Override
        public void onDataFailed(Exception e) {
            System.out.println(e);
        }
    });

# 7) Watch Directory to Detect File Remove in SubFolders
    dataFiles.setOnDataRemoveSubFolderChangeListener(new addOnDataRemoveSubFolderChangeListener() {
        @Override
        public void onDataRemoved(File file, String name) {
            System.out.println("Change : "+file.getAbsolutePath());
        }

        @Override
        public void onDataRemovedFailed(Exception e) {
            System.out.println(e);
        }
    });



#Try It Out
Because this API is more advanced, try it out before proceeding.
