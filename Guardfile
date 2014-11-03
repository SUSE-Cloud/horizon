TARGET = ENV['GUARD_RSYNC_TARGET']
raise 'Must set GUARD_RSYNC_TARGET to horizon host' if TARGET.nil? or TARGET.empty?

group('assets') do
  assets_sync_opts = {
    :sync_on_start => true,

    :source => 'openstack_dashboard/static/dashboard/',
    :destination => '/srv/www/openstack-dashboard/openstack_dashboard/static/dashboard',

    :user => TARGET.split('@', 2).first,
    :remote_address => TARGET.split('@', 2).last,
    :verbose => false,
    :dry_run => false,
    :exclude_from => nil
  }

  guard('remote-sync', assets_sync_opts) do
    watch(%r{^openstack_dashboard/static/dashboard/.+})
  end
end

group('templates') do
  assets_templates_opts = {
    :sync_on_start => true,

    :source => 'openstack_dashboard/templates/',
    :destination => '/srv/www/openstack-dashboard/openstack_dashboard/templates',

    :user => TARGET.split('@', 2).first,
    :remote_address => TARGET.split('@', 2).last,
    :verbose => false,
    :dry_run => false,
    :exclude_from => nil
  }

  guard('remote-sync', assets_templates_opts) do
    watch(%r{^openstack_dashboard/templates/.+})
  end
end
