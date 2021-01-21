# intrusion
## Intrusion. Custom Asterisk dial plan for listen, whisper and barge in calls. For FreePBX, Issabel, Asterisk based Elastix call centers.

If you are running a call center on FreePBX or Asterisk, most likely you will want the ability to listen in on agents calls, also known as joining multiple calls, or connected two calls to a manager, or other variations of barging in on a bridged channel.

For the purpose of this article, we will define manager as the callee who is the spying channel, agent who is the spied-on channel, and client who is the bridged channel / 3rd party. We define listen, whisper, and barge as follows:

Listen: Monitor an agents call. The manager can hear both the agent and client channels, but no-one can hear the manager.

Whisper:  Whisper to the agent. The manager can hear both the agent and client channels, and the agent can also hear the manager, but the client can only hear the agent, hence “whisper.”

Barge: Barge in on both channels. The manager channel is joined onto the agent and client channels, and all parties can hear each other. Be warned, if the original agent leaves the call, the call is dropped. This is not a 3-way call.
(However you can barge in, and when comfortable, initiate a 3way call to your extension so you can continue the call without the agent. This procedure varies from client to client (soft/hard phones))

Note: In newer versions of FreePBX, custom includes are disabled by default.
This means that the new “ext-local-custom” context’s that we are about to create won’t be imported into the PBX “Brain”. To fix this, go to :
Settings->Advanced Settings
Find the “Dialplan and Operational” section, and change Disable -custom Context Includes? to False.
Be sure to click on the little checkbox that appears to the right to save the setting, then Apply Settings to rebuild the files. This is required or else the ext-local-custom context that we add won’t be included into the engine.

This should be placed in /etc/asterisk/extensions_custom.conf for FreePBX
