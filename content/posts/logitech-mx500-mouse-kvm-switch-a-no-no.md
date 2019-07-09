---
title: 'Logitech MX500 Mouse & KVM switch a no-no'
date: Wed, 07 Jul 2004 22:03:57 +0000
draft: false
tags: [Linux]
categories: [Linux]
type: post
---

I got rid of my IBM Scrollpoint III mouse which was flakey because of it's scroll "stick" instead of a wheel. I replaced it with a new [Logitech MX500 Optical Mouse](http://www.newegg.com/app/Showimage.asp?image=26-104-129-05.jpg/26-104-129-02.JPG/26-104-129-04.JPG/26-104-129-03.JPG/26-104-129-06.JPG). I have one of these mice at work running on RHEL 3. Liz has one working with Windows XP Pro. So imagine my surprise when it didn't want to work with [Fedora Core 2](http://fedora.redhat.com). I almost crapped myself.

I decided to try it with Windows XP. And the MouseWare driver auto detected a 2-button Logitech basic mouse. Logitech's website gave me a clue to the potential problem:

> Unfortunately, Logitech does not provide technical support for any of our products when connected to a pass-through device. A pass-through device can be thought of as any device that the Logitech device plugs into and then is interfaced or plugged into the computer. The reason for this is that these devices can interfere with communication between the Logitech device and the computer. Examples of a pass-through device are switch boxes, extension cables, KVM (Keyboard Video and mouse combination) switches, port replicators, third party port adapters or converters and y-adapters.
> 
> If you have a passthrough device and the Logitech device is not functioning correctly, please connect the Logitech device directly to the system for testing. If the Logitech device works correctly when connected directly to the system but does not work correctly when connected to the passthrough device, please contact the manufacturer of the passthrough device for further diagnostics.
> 
> If you do not have a passthrough device and are planning to purchase one, please be aware that your Logitech product may not work correctly through it. Different manufacturers implement device support differently, which can affect the functionality of your Logitech device.

I unplugged the mouse from the KVM and directly into the machine. Rebooted Windows XP and the MouseWare drivers now recognized the mouse correctly. I promptly rebooted into Linux and all was right with the world.