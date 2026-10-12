# Queues (Workflow)

A queue is a to-do list shared by a team. It shows which records are waiting for
you, who put them there and how long they have waited. Linked together, queues set
a path that every booking, order or bill follows.

## Working your queues

1. Open **Queues** under Inbound, Processing, Outbound or Documentation. Each lists
   the queues for that stage, with how many items are waiting and how many are
   overdue.
2. Open a queue. Items waiting longer than the queue allows are marked overdue.
3. Open an item and do your part.
4. Back in the queue, select the items you finished and click **Next Queue**. They
   move to the next queue. If there is no next queue, they leave the queue.

You can also add a record to a queue, or take it out, with the **Queues** button on
the record itself.

**Set Completed** stamps a Completed date on the selected items. Posted items are
skipped.

> **Screenshot placeholder:** a queue page with a few items selected and the Next Queue button. (save as `images/queue.png`)

## Good to know

- Always use **Next Queue** to move work along. Taking an item out and adding it to
  the next queue loses the history of how it got there. Take an item out only if it
  was added too early, or to send it back to whoever started it.
- New records start in the queues marked as starting points for their kind (new
  agreements of a type, new bills of a type, new bookings).
- An item's waiting time counts from when it was first added, not from when it
  reached the current queue. **Next Queue** keeps that time.
- An *Add to Queue* scheduled job runs when an item is added to its queue, not when
  an item arrives there through **Next Queue**.
- A queue isn't a status. A completed booking shouldn't be in any queue.
- Bookings watched with the shipline go into the remote-changes queue when the
  carrier reports a change.

## Who sees what

Each queue lists two sets of roles:

- **Roles that see and work it.** Only these roles see the queue and its items. If
  empty, everyone does.
- **Roles that may add.** Only these roles can put items into the queue, including
  moving items into it with Next Queue. If empty, everyone can.

To move items on with **Next Queue**, you need to be allowed to add to the next
queue. Someone with the Queues setup feature at its highest level sees every queue,
but can only work the ones their roles allow.

See also: [Queues](../context/Q002.md), [Queue setup](../context/Q001.md).
