Deployment:

Verify that okTrigIn.db does not RESET any scopes: $(S1){$(D1)}Rst:Sc-Cmd

Verify that st.cmd okCircBuf.db prefix S2 refers to Global RF (GRF), not to Local RF (LRF).

Verify that okCloseLoop.db does not refer to any production EVR! (Search for EVR!)

Uncomment okCircBuf.db the link to E-Launcher.
 
procServ -n SR-CFCA -LSR-CFCA.log -i ^D^C 4051 ./st.cmd  &


