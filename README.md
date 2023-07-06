# Distributed `k-means` with PySpark
`README` for internal use.
        ____                                   __   __         
       / __ \____ _      _____  ________  ____/ /  / /_  __  __
      / /_/ / __ \ | /| / / _ \/ ___/ _ \/ __  /  / __ \/ / / /
     / ____/ /_/ / |/ |/ /  __/ /  /  __/ /_/ /  / /_/ / /_/ / 
    /_/    \____/|__/|__/\___/_/   \___/\__,_/  /_.___/\__, /  
       __________  ____  __  ______     _   _______   /____/__ 
      / ____/ __ \/ __ \/ / / / __ \   / | / /  _/ | / / ____/ 
     / / __/ /_/ / / / / / / / /_/ /  /  |/ // //  |/ / __/    
    / /_/ / _, _/ /_/ / /_/ / ____/  / /|  // // /|  / /___    
    \____/_/ |_|\____/\____/_/      /_/ |_/___/_/ |_/_____/

## The CloudVeneto Experience: a quick checklist

1. Open a terminal and enter the CV gate machine:
       ssh gbordin@gate.cloudveneto.it
   When prompted, enter the longer password.
2. When inside, access the VM of your choice – usually the `master` – with
       ssh -i private/gbordin.pem bordin@10.67.22.239
   Use the shorter password this time. If for some reason you want to
   access the slaves right away, just substitute their IP address on the
   right of the @. The command prompt should change to
       bordin@mapd-b-2023-gr04-1:~$
   or `gr04-2`/`gr04-3` if you accessed the slaves.
4. Start the cluster by running the script `start_cluster`.
5. Enter the command `sparkup`: it should open a jupyter-notebook session
   on the 9999 port of the VM.
6. Open a new terminal and re-enter the cloud by skipping right to the VM,
   defining also the tunnelling ports:
       ssh -J gbordin@gate.cloudveneto.it \
           -L aaaa:localhost9999 \
           -L bbbb:localhost:8080 \
           -L cccc:localhost:4040 \
           bordin@10.67.22.239
   Substitute `aaaa`, `bbbb` and `cccc` with the ports of your choice.
   `aaaa` is for the Jupyter notebook, `bbbb` for the Spark master page and
   `cccc` for the workers’ dashboard.
7. Open `localhost:aaaa` (`bbbb`, `cccc`) on your browser and you should
   be able to access the Jupyter session and the Spark stuff.
8. When you finish your work, remember to stop the cluster by running the
   `stop_cluster` script from the `master` VM.

You can jump between the VMs when you’re inside with `ssh master`, `ssh
slave01` or `ssh slave02`. This is useful when you have to install new
Python packages, because you have to do it *on all three machines*.
