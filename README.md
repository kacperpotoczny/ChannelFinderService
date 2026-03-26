# Tutorials

ChannelFinder is a directory server, implemented as a REST style web service.
Its intended use is for control systems, namely the EPICS Control system.

- [Documentation](https://channelfinder.readthedocs.io/en/latest/)
- [Releases](https://github.com/ChannelFinder/ChannelFinderService/releases)
- [Docker Containers](https://github.com/ChannelFinder/ChannelFinderService/pkgs/container/channelfinderservice)

## Description

* **Motivation and Objectives**

  High level applications tend to prefer a hierarchical view of the control system name space. They group channel names
  by location or physical function. The name space of the EPICS Channel Access protocol, on the other hand, is flat. A
  good and thoroughly enforced naming convention may solve the problem of creating unique predictable names. It does not
  free every application from being configured explicitly, so that it knows all channel names it might be interested in
  beforehand.

  ChannelFinder tries to overcome this limitation by implementing a generic directory service, which applications can
  query for a list of channels that match certain conditions, such as physical functionality or location. It also
  provides mechanisms to create channel name aliases, allowing for different perspectives of the same set of channel
  names.

* **Directory Data Structure**

  Each directory entry consists of a channel `<name>`, an arbitrary set of `<properties>` (name-value pairs), and an
  arbitrary set of `<tags>` (names).

* **Basic Operation**

  An application sends an HTTP query to the service, specifying an expression that references tags, properties and their
  values, or channel names. The service returns a list of matching channels with their properties and tags, as JSON
  documents.
  
  
## Documentation and instructions
Documentetion, operation instructions, build instructions and manuals has been moved to [readthedocs](https://channelfinder.readthedocs.io/en/latest/)
