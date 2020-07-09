I want to use gcp compute engine's shutdown script to deregister itself from nomad cluster when the machine shuts down 
(e.g., when I upgrade the managed instance template). But this does not work for me.

After several hours or trying, I find the rootcase: it cannot deregister itself because when the shutdown script is running, 
there's no nomad process running on the instance anymore. I only find it out when I manually create a instance in the stack, so the disk is preserved.

Worth pointing out the way to get shutdown script logs:
```
sudo journalctl -u google-shutdown-scripts.service
```
